[Depths of Doom (2).html](https://github.com/user-attachments/files/33364594/Depths.of.Doom.2.html)
# dungeon<!DOCTYPE html>
<html lang="en"><head><meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1, viewport-fit=cover">
<title>Depths of Doom</title>
<link href="https://fonts.googleapis.com/css2?family=Press+Start+2P&display=swap" rel="stylesheet">
<style>
:root{box-sizing:border-box;padding-top:env(safe-area-inset-top,0px);padding-bottom:env(safe-area-inset-bottom,0px);--bg:#0b0907;--pan:#1a1410;--bd:#4a3a28;--tx:#efe3c8;--mu:#9b8a6c;--gold:#e3b04b;--red:#d9402b;--grn:#4fbf5f;--t0:#9aa0a6;--t1:#5ec26a;--t2:#4aa3ff;--t3:#b56cff;--t4:#ffb830;--f:'Press Start 2P','Courier New',monospace}
html{scroll-padding-top:env(safe-area-inset-top,0px)}
*{box-sizing:border-box}
body{margin:0;background:var(--bg);color:var(--tx);font:15px/1.4 Georgia,serif;-webkit-tap-highlight-color:transparent}
main{max-width:560px;margin:0 auto;padding:10px;position:relative}
.top{display:flex;justify-content:space-between;align-items:center;font-family:var(--f);margin-bottom:8px}
.top h1{font-size:18px;margin:0;color:var(--gold);letter-spacing:2px}
#pips{display:flex;gap:6px;align-items:center;font-size:12px;color:var(--mu)}
#pips i{width:14px;height:14px;border-radius:50%;border:2px solid var(--bd);background:#000}
#pips i.d{background:var(--gold);border-color:var(--gold)}#pips i.c{border-color:var(--red);box-shadow:0 0 8px var(--red)}
#pips i.b{border-radius:3px}
#stage{position:relative;height:300px;border:3px solid var(--bd);border-radius:12px;overflow:hidden;
 background:radial-gradient(ellipse at 50% 45%,rgba(255,150,50,.18),transparent 60%),
 repeating-linear-gradient(0deg,rgba(0,0,0,.35) 0 2px,transparent 2px 40px),
 repeating-linear-gradient(90deg,rgba(0,0,0,.25) 0 2px,transparent 2px 70px),#2a211a;box-shadow:inset 0 0 70px #000}
#stage::after{content:"";position:absolute;left:0;right:0;bottom:0;height:70px;background:linear-gradient(transparent,#120d09 80%)}
.torch{position:absolute;top:30px;font-size:34px;animation:fl .15s infinite alternate;filter:drop-shadow(0 0 14px #ff8a1f)}
.torch.l{left:18px}.torch.r{right:18px;animation-delay:.07s}
@keyframes fl{from{transform:scale(1) rotate(-3deg);opacity:.9}to{transform:scale(1.12) rotate(3deg);opacity:1}}
#mon{position:absolute;left:50%;top:70px;transform:translateX(-50%);text-align:center;z-index:2}
#me{font-size:110px;line-height:1;display:inline-block;animation:bob 2.2s ease-in-out infinite;filter:drop-shadow(0 12px 10px #000)}
#mon.boss #me{font-size:140px;filter:drop-shadow(0 0 22px var(--red)) drop-shadow(0 12px 10px #000)}
@keyframes bob{50%{transform:translateY(-8px)}}
#mon.hit #me{animation:hit .35s}#mon.die #me{animation:die .7s forwards}
@keyframes hit{0%,100%{transform:translateX(0);filter:brightness(1)}20%{transform:translateX(-14px);filter:brightness(3)}60%{transform:translateX(12px)}}
@keyframes die{to{transform:translateY(40px) scale(.2) rotate(90deg);opacity:0}}
#mon.atk #me{animation:lunge .35s}
@keyframes lunge{40%{transform:translateY(60px) scale(1.25)}}
#mbar{width:200px;margin:2px auto 0}
.mname{font-family:var(--f);font-size:14px;text-shadow:0 2px 4px #000}
#mon.boss .mname{color:var(--red);font-size:16px}
.bar{height:14px;background:#000;border:2px solid var(--bd);border-radius:8px;overflow:hidden;position:relative}
.bar i{display:block;height:100%;transition:width .35s;background:linear-gradient(#ff6a4f,#a52714)}
.bar.p i{background:linear-gradient(#7fe08c,#2f8c3c)}
.bar.x{height:7px}.bar.x i{background:linear-gradient(#ffd56a,#b8860b)}
.bar span{position:absolute;inset:0;text-align:center;font:bold 10px/10px sans-serif;color:#fff;text-shadow:0 1px 2px #000}
#hero{position:absolute;left:24px;bottom:14px;font-size:52px;z-index:3;filter:drop-shadow(0 6px 5px #000)}
#hero.atk{animation:hl .35s}#hero.hurt{animation:hr .35s}
@keyframes hl{40%{transform:translate(90px,-60px) rotate(15deg)}}
@keyframes hr{30%{transform:translateX(-12px);filter:brightness(2.5) hue-rotate(-40deg)}}
.fl{position:absolute;font:800 28px var(--f);z-index:6;pointer-events:none;animation:up 1s forwards;text-shadow:0 2px 0 #000,0 0 8px #000}
@keyframes up{to{transform:translateY(-70px);opacity:0}}
#flash{position:absolute;inset:0;z-index:5;background:var(--red);opacity:0;pointer-events:none}
#flash.on{animation:fa .35s}@keyframes fa{from{opacity:.45}to{opacity:0}}
#stage.shake{animation:sh .3s}@keyframes sh{25%{transform:translate(-6px,3px)}75%{transform:translate(6px,-3px)}}
.panel{background:var(--pan);border:2px solid var(--bd);border-radius:12px;padding:10px;margin-top:10px}
.prow{display:flex;justify-content:space-between;font-family:var(--f);font-size:14px;margin-bottom:5px}
.slots{display:grid;grid-template-columns:repeat(3,1fr);gap:8px;margin-top:10px}
.slot{background:#0d0a07;border:2px solid var(--c,var(--bd));border-radius:10px;padding:6px;text-align:center;box-shadow:inset 0 0 14px color-mix(in srgb,var(--c,#000) 35%,transparent)}
.slot b{display:block;font-size:22px}.slot small{display:block;color:var(--mu);font-size:10px;text-transform:uppercase;letter-spacing:1px}
.slot span{font-size:12px;color:var(--c,var(--tx));font-weight:bold}.slot em{display:block;font-size:11px;color:var(--mu);font-style:normal}
#btns{display:grid;grid-template-columns:repeat(4,1fr);gap:8px;margin-top:10px}
button{font:inherit;color:var(--tx);cursor:pointer;background:linear-gradient(#3a2c1f,#1f1710);border:2px solid var(--bd);border-radius:10px;padding:8px 2px;text-align:center;transition:transform .08s}
button:hover:not(:disabled){border-color:var(--gold);transform:translateY(-2px)}
button:active:not(:disabled){transform:translateY(1px)}
button:disabled{opacity:.35;cursor:default}
button b{display:block;font-size:26px;line-height:1.1}button span{font:600 11px var(--f)}button small{display:block;font-size:9px;color:var(--mu)}
#log{height:70px;overflow-y:auto;margin-top:10px;font-size:13px;color:var(--mu);background:#0d0a07;border:1px solid var(--bd);border-radius:8px;padding:6px 8px}
#log p{margin:1px 0}#log p:last-child{color:var(--tx)}
#ov{position:fixed;inset:0;z-index:20;background:rgba(5,3,2,.9);display:flex;align-items:center;justify-content:center;text-align:center;padding:20px}
#ov.hide{display:none}
#ov div{max-width:360px}#ov h2{font:800 34px var(--f);margin:6px 0;color:var(--gold);letter-spacing:2px}
#ov p{color:var(--mu)}#ov button{padding:14px 34px;font:800 18px var(--f);margin-top:10px;border-color:var(--gold)}
#ov .big{font-size:70px}
#toast{position:absolute;left:50%;top:10px;transform:translate(-50%,-30px);z-index:10;opacity:0;background:#000d;border:2px solid var(--c,var(--gold));color:var(--c,var(--gold));border-radius:10px;padding:8px 14px;font:700 14px var(--f);text-align:center;transition:.35s;pointer-events:none;white-space:nowrap}
#toast.on{opacity:1;transform:translate(-50%,0)}
@media(max-width:380px){#me{font-size:90px}button b{font-size:22px}}
*{border-radius:0!important}
body{font:10px/1.6 var(--f)}
img.px{display:block;margin:0 auto;image-rendering:pixelated;filter:drop-shadow(2px 0 0 #000) drop-shadow(-2px 0 0 #000) drop-shadow(0 2px 0 #000) drop-shadow(0 -2px 0 #000)}
#mon.boss img.px{filter:drop-shadow(3px 0 0 var(--red)) drop-shadow(-3px 0 0 var(--red)) drop-shadow(0 3px 0 var(--red)) drop-shadow(0 -3px 0 var(--red))}
#me,#hero,.torch,#mon.boss #me{filter:none}#me{line-height:0}
.top{flex-wrap:wrap;gap:6px}.top h1{font-size:11px;letter-spacing:0}
#pips{gap:4px}#pips i{width:10px;height:10px;border-width:2px}#pips span{font-size:8px}
#stage{border:4px solid #000;outline:4px solid var(--bd);box-shadow:none;background:repeating-linear-gradient(0deg,#1c140e 0 4px,transparent 4px 36px),repeating-linear-gradient(90deg,#1c140e 0 4px,transparent 4px 72px),#3b2e22}
#stage::after{height:64px;background:#120d09;border-top:4px solid #000}
@keyframes fl{from{transform:translateY(0)}to{transform:translateY(-4px)}}
@keyframes hl{40%{transform:translate(90px,-60px)}}
@keyframes lunge{40%{transform:translateY(60px)}}
.torch{animation:fl .3s steps(2) infinite alternate}
#me{animation:bob 1s steps(2) infinite}
#mon.hit #me{animation:hit .4s steps(5)}#mon.die #me{animation:die .7s steps(7) forwards}#mon.atk #me{animation:lunge .4s steps(4)}
#hero.atk{animation:hl .4s steps(4)}#hero.hurt{animation:hr .4s steps(4)}
.fl{font:16px var(--f);animation:up 1s steps(10) forwards;text-shadow:3px 3px 0 #000}
#flash.on{animation:fa .4s steps(3)}#stage.shake{animation:sh .3s steps(4)}
.mname{font-size:10px;text-shadow:2px 2px 0 #000}#mon.boss .mname{font-size:11px}
.bar{height:18px;border:3px solid #000;background:#2a1812;outline:2px solid var(--bd)}.bar.x{height:10px}
.bar i{background:repeating-linear-gradient(90deg,transparent 0 6px,rgba(0,0,0,.3) 6px 8px),#d9402b;transition:width .4s steps(8)}
.bar.p i{background:repeating-linear-gradient(90deg,transparent 0 6px,rgba(0,0,0,.3) 6px 8px),#4fbf5f}
.bar.x i{background:repeating-linear-gradient(90deg,transparent 0 6px,rgba(0,0,0,.3) 6px 8px),#e3b04b}
.bar span{font:7px/12px var(--f)}
.panel{border:4px solid #000;outline:3px solid var(--bd)}.prow{font-size:8px;gap:6px}
.slot{border:3px solid var(--c,var(--bd));box-shadow:none}.slot small{font-size:6px;letter-spacing:0}.slot span{font-size:7px}.slot em{font-size:6px;margin-top:2px}.slot span,.slot em{word-break:break-word}
button{font-family:var(--f);border:4px solid #000;background:#4a3828;box-shadow:inset -4px -4px 0 rgba(0,0,0,.35),inset 4px 4px 0 rgba(255,255,255,.12)}
button:hover:not(:disabled){background:#5e4932;transform:none;outline:3px solid var(--gold);border-color:#000}
button:active:not(:disabled){transform:translateY(2px)}
button b{display:flex;justify-content:center;font-size:0;margin-bottom:4px}button span{font:8px var(--f)}button small{font-size:6px;margin-top:3px}
#log{height:84px;font-size:9px;border:3px solid #000;outline:2px solid var(--bd)}
#ov h2{font:18px/1.3 var(--f);letter-spacing:0}#ov p{font-size:9px;line-height:1.9}#ov button{font:12px/1.4 var(--f)}
#ov .big{display:flex;justify-content:center;gap:8px;font-size:0}
#toast{font:9px/1.7 var(--f);border:4px solid var(--c,var(--gold));background:#000}#toast img{display:inline-block;vertical-align:middle;margin:0 6px 0 0}
#home{position:fixed;inset:0;z-index:30;display:flex;text-align:center;padding:20px;overflow-y:auto;background:radial-gradient(circle at 50% 30%,rgba(255,140,40,.22),transparent 55%),repeating-linear-gradient(0deg,#1c140e 0 4px,transparent 4px 36px),repeating-linear-gradient(90deg,#1c140e 0 4px,transparent 4px 72px),#0e0a07}
#home.hide,#help.hide{display:none}
.hc{width:100%;max-width:340px;margin:auto}
.logo{font:26px/1.35 var(--f);color:var(--gold);text-shadow:4px 4px 0 #7a1f10,7px 7px 0 #000}
.tag{font-size:8px;color:var(--mu);margin-top:14px}
#hsp{display:flex;gap:16px;align-items:flex-end;justify-content:center;margin:22px 0}
#hsp div{animation:bob 1s steps(2) infinite}#hsp div:nth-child(2){animation-delay:.3s}#hsp div:nth-child(3){animation-delay:.6s}
.menu{display:grid;gap:10px}.menu button{padding:14px 6px;font:11px var(--f)}
#hCont:not(:disabled){border-color:var(--gold)}
#help{margin-top:14px;text-align:left;font-size:8px;line-height:2;background:#0d0a07;border:3px solid #000;outline:2px solid var(--bd);padding:10px}
#hstat{margin-top:14px;font-size:8px;color:var(--mu)}
#menu{margin-left:auto;padding:4px 8px;font:8px var(--f)}
:root{--bg:#5a4a7a;--pan:#6e5c92;--bd:#b79ae0;--tx:#fffbe8;--mu:#eadff9;--gold:#ffd84a;--red:#ff5a40;--t0:#dfe3e8;--t1:#7bff8a;--t2:#63b8ff;--t3:#e0a8ff;--t4:#ffc83a}
body{background:linear-gradient(#7a68a3,#4f3f70) fixed}
#stage{background:radial-gradient(circle at 50% 40%,rgba(255,245,180,.5),transparent 62%),repeating-linear-gradient(0deg,#a58258 0 4px,transparent 4px 36px),repeating-linear-gradient(90deg,#a58258 0 4px,transparent 4px 72px),#cfae82}
#stage::after{background:#8a6a48;border-top:4px solid #5a4028}
.bar{background:#3a2b52}.slot,#log,#help{background:#54447a}#log p:last-child{color:#fff}
#pips i{background:#3a2b52}
button{background:#8266c0}button:hover:not(:disabled){background:#9a7ddb}
#ov{background:rgba(70,55,105,.9)}#toast{background:#3a2b52}
#home{background:radial-gradient(circle at 50% 30%,rgba(255,230,130,.6),transparent 62%),repeating-linear-gradient(0deg,#9585b8 0 4px,transparent 4px 36px),repeating-linear-gradient(90deg,#9585b8 0 4px,transparent 4px 72px),#7766a0}
#bagb{width:100%;margin-top:8px;padding:10px;font:9px var(--f)}
#bg{position:fixed;inset:0;z-index:25;background:rgba(60,45,95,.9);display:flex;padding:12px;overflow-y:auto}#bg.hide{display:none}
#bgc{margin:auto;width:100%;max-width:520px;background:var(--pan);border:4px solid #000;outline:3px solid var(--bd);padding:12px}
#bgc h3{font:9px var(--f);color:var(--gold);margin:14px 0 4px}#bgc p{font-size:7px;color:var(--mu);margin:6px 0 0}
.it{display:flex;align-items:center;gap:10px;margin:6px 0;padding:6px;border:3px solid var(--c);background:rgba(0,0,0,.25);cursor:pointer}.it.eq{background:rgba(255,255,255,.2)}
.it img{margin:0;flex:none}.it>div{flex:1;min-width:0}.it b{display:block;font-size:9px;color:var(--c);margin-bottom:4px}.it small{font-size:7px;color:var(--mu);line-height:1.6}.it>span{font-size:7px;color:var(--gold)}
:root{--wl:#cfae82;--wm:#a58258;--wf:#8a6a48;--t5:#5ff3ff;--t6:#ff8a3a;--t7:#e07dff}
#stage{background:radial-gradient(circle at 50% 40%,rgba(255,245,180,.5),transparent 62%),repeating-linear-gradient(0deg,var(--wm) 0 4px,transparent 4px 36px),repeating-linear-gradient(90deg,var(--wm) 0 4px,transparent 4px 72px),var(--wl)}
#stage::after{background:var(--wf)}
#ptl{position:fixed;inset:0;z-index:50;background:#000;opacity:0;overflow:hidden}#ptl.hide{display:none}
#ptl.on{animation:pin 3.8s steps(19) forwards}
@keyframes pin{0%{opacity:0}8%,88%{opacity:1}100%{opacity:0}}
#rg{position:absolute;left:50%;top:50%;width:260px;height:260px;margin:-130px 0 0 -130px;animation:rgz 3.8s steps(19) forwards}
@keyframes rgz{0%{transform:scale(.1)}30%{transform:scale(1)}58%{transform:scale(1.4)}100%{transform:scale(9)}}
#rg i{position:absolute;border:10px solid var(--pc);animation:rr 1s steps(6) infinite}
#rg i:nth-child(1){inset:0}#rg i:nth-child(2){inset:36px;animation-direction:reverse;border-color:#fff}#rg i:nth-child(3){inset:72px}#rg i:nth-child(4){inset:108px;animation-direction:reverse;background:#000}
@keyframes rr{to{transform:rotate(90deg)}}
#ph{position:absolute;left:50%;top:50%;margin:-36px 0 0 -36px;animation:phh 3.8s steps(19) forwards}
@keyframes phh{0%,25%{transform:translate(-130px,90px) rotate(0deg) scale(1)}60%{transform:translate(0,0) rotate(720deg) scale(.15)}100%{transform:translate(0,0) rotate(900deg) scale(0)}}
#pf{position:absolute;inset:0;opacity:0;animation:pff 3.8s steps(19) forwards}
@keyframes pff{0%,56%{opacity:0;background:#fff}62%{opacity:1;background:#fff}72%,100%{opacity:1;background:var(--pc)}}
#ptt,#ptw{position:absolute;left:0;right:0;text-align:center;opacity:0;animation:ptx 3.8s steps(19) forwards}
#ptt{top:36%;font:10px var(--f);color:#fff;text-shadow:2px 2px 0 #000}#ptw{top:44%;font:18px/1.4 var(--f);color:#fff;text-shadow:4px 4px 0 #000}
@keyframes ptx{0%,70%{opacity:0}76%,92%{opacity:1}100%{opacity:0}}
:root{--t8:#fff6a0}
@keyframes hb{50%{transform:translateY(-4px)}}#hero{animation:hb 1s steps(2) infinite}
:root{--t8:#9be85a;--t9:#ffcf6a;--t10:#4ad8ff;--t11:#fff6a0}
.wi{display:block;margin:0 auto;image-rendering:auto;filter:drop-shadow(0 2px 2px rgba(0,0,0,.45))}
.wi.sh{animation:shim 2.4s ease-in-out infinite}
@keyframes shim{0%,100%{filter:drop-shadow(0 2px 2px rgba(0,0,0,.45)) brightness(1)}50%{filter:drop-shadow(0 0 7px var(--sc)) drop-shadow(0 0 2px var(--sc)) brightness(1.3)}}
#fz{position:fixed;inset:0;z-index:35;background:rgba(60,45,95,.94);display:flex;padding:12px;overflow-y:auto}#fz.hide{display:none}
#fzc{margin:auto;width:100%;max-width:520px;background:var(--pan);border:4px solid #000;outline:3px solid var(--bd);padding:12px}
.fzh{display:flex;justify-content:space-between;align-items:center;font:12px var(--f);color:var(--gold)}
.fzt{display:flex;gap:6px;margin:10px 0}.fzt button{flex:1;padding:8px;font-size:8px}.fzt button.on{border-color:var(--gold);background:#a085e0}
.fzc{display:flex;align-items:center;justify-content:center;gap:8px;margin:12px 0;padding:10px;background:#3a2b52;border:3px solid #000;position:relative;overflow:hidden}
.fzs{width:62px;height:62px;border:3px dashed var(--bd);display:flex;align-items:center;justify-content:center;font:10px var(--f);color:var(--mu)}.fzs.f{border:3px solid var(--c)}
.fzc .ar{font:14px var(--f);color:var(--gold)}
.fzc.go .fzs:not(#fzo){animation:fzg .9s steps(9) forwards}
@keyframes fzg{0%{transform:none}70%{transform:translateX(var(--mx)) scale(.6) rotate(360deg)}100%{transform:translateX(var(--mx)) scale(0) rotate(720deg)}}
.fzc.go::after{content:'';position:absolute;inset:0;background:#fff;opacity:0;animation:fzf .95s steps(10) forwards}
@keyframes fzf{0%,70%{opacity:0}80%{opacity:1}100%{opacity:0}}
.it.sel{outline:3px solid var(--gold)}.it.dim{opacity:.35}
:root{--t12:#fff}
#stage.divine::before{content:'';position:absolute;left:-50%;top:-80%;width:200%;height:260%;background:repeating-conic-gradient(from 0deg at 50% 45%,rgba(255,244,170,.38) 0 7deg,transparent 7deg 22deg);animation:rays 30s steps(120) infinite;z-index:1;pointer-events:none}
@keyframes rays{to{transform:rotate(360deg)}}
#mon.god{top:30px}
#stage.hyb #mon{opacity:0;pointer-events:none}
.hh{position:absolute;transform:translateX(-50%);text-align:center;width:80px;cursor:pointer;z-index:2}.hh small{display:block;font-size:6px;color:#fff;text-shadow:1px 1px 0 #000}.hbar{height:7px;border:2px solid #000;background:#3a2b52;margin:0 8px}.hbar i{display:block;height:100%;background:#e8452a;transition:width .3s steps(6)}.hh.dead{opacity:.28;filter:grayscale(1);pointer-events:none}.hh.tg{outline:3px dashed var(--gold)}.hh.hit img{animation:hit .4s steps(5)}
#hyi{position:absolute;left:6px;top:4px;font:7px/1.6 var(--f);color:#fff;text-shadow:2px 2px 0 #000;z-index:4}
#hy{position:fixed;inset:0;z-index:36;background:rgba(60,45,95,.96);display:flex;padding:12px;overflow-y:auto}#hy.hide{display:none}
#hyc{margin:auto;width:100%;max-width:480px;background:var(--pan);border:4px solid #000;outline:3px solid var(--bd);padding:14px;text-align:center}
#hyc p{font-size:8px;line-height:1.9;color:var(--mu)}#hyc button.w{width:100%;padding:12px;margin-top:8px;font-size:10px}#hyc input{width:100%;box-sizing:border-box;padding:10px;font:12px var(--f);text-align:center;text-transform:uppercase;background:#2a1f3d;color:#fff;border:3px solid #000;margin-top:8px}
#cs{position:fixed;inset:0;z-index:60;background:#05030c}#cs.hide{display:none}#csc{position:absolute;inset:0;width:100%;height:100%}
#cst{position:absolute;left:0;right:0;top:10%;text-align:center;font:13px/1.9 var(--f);color:#fff;text-shadow:3px 3px 0 #000;padding:0 14px}
#csi{position:absolute;left:0;right:0;bottom:4%;display:flex;flex-wrap:wrap;gap:8px;justify-content:center;padding:0 8px;max-height:62%;overflow:auto}
.cc{width:128px;padding:8px;border:3px solid #fff;background:rgba(11,7,32,.85);text-align:center;opacity:0;animation:cin .7s steps(7) forwards}.cc b{display:block;font:8px var(--f);margin-top:4px}.cc small{font:7px var(--f);color:#ccc}
@keyframes cin{from{opacity:0;transform:translateY(40px) scale(.5)}to{opacity:1;transform:none}}
#stage.hyb .torch{display:none}
:root{--t13:#ff4a2a;--t14:#ffd700}
#stage.hellp::before{content:'';position:absolute;left:-50%;top:-80%;width:200%;height:260%;background:repeating-conic-gradient(from 0deg at 50% 45%,rgba(255,60,20,.35) 0 6deg,transparent 6deg 20deg);animation:rays 24s steps(120) infinite reverse;z-index:1;pointer-events:none}
#stage.hellp::after{background:linear-gradient(#ff8a2a,#a02010);animation:lava 1s steps(2) infinite}
@keyframes lava{50%{filter:brightness(1.35)}}
</style></head>
<body><main>
<div class="top"><h1>DEPTHS OF DOOM</h1><div id="pips"></div><button id="menu" onclick="if(!busy)home()">MENU</button></div>
<div id="stage">
 <div class="torch l"></div><div class="torch r"></div>
 <div id="toast"></div><div id="flash"></div>
 <div id="mon"><div id="me"></div><div class="mname" id="mn"></div><div id="mbar" class="bar"><i id="mb"></i><span id="mt"></span></div></div>
 <div id="hero"></div>
</div>
<div class="panel">
 <div class="prow"><span>Hero · Lv <span id="lv"></span></span><span id="fn" style="color:var(--mu)"></span></div>
 <div class="bar p"><i id="pb"></i><span id="pt"></span></div>
 <div class="bar x" style="margin-top:5px"><i id="xb"></i></div>
 <div class="slots" id="slots"></div>
</div>
<div id="btns"></div><button id="bagb" onclick="if(!busy)openBag()">BAG</button>
<div id="log"></div>
</main>
<div id="ov"><div id="ovc"></div></div>
<div id="ptl" class="hide"><div id="rg"><i></i><i></i><i></i><i></i></div><div id="ph"></div><div id="pf"></div><div id="ptt"></div><div id="ptw"></div></div>
<div id="bg" class="hide"><div id="bgc"></div></div>
<div id="hy" class="hide"><div id="hyc"></div></div><div id="cs" class="hide"></div>
<div id="fz" class="hide"><div id="fzc"></div></div>
<div id="home"><div class="hc">
 <div class="logo">DEPTHS<br>OF DOOM</div>
 <div class="tag">A PIXEL DUNGEON CRAWLER</div>
 <div id="hsp"></div>
 <div class="menu">
  <button id="hCont" onclick="cont()">CONTINUE</button>
  <button onclick="newGame()">NEW GAME</button>
  <button id="hFuse" onclick="openFz()">FUSE ITEMS</button>
  <button onclick="hyOpen()">BOSS MODE</button>
  <button onclick="$('help').classList.toggle('hide')">HOW TO PLAY</button>
 </div>
 <div id="help" class="hide">&gt; Fight monsters to level up and loot gear.<br>&gt; Weapons add attack. Armour cuts damage.<br>&gt; HEAVY: 60% hit, x1.8 damage. GUARD: half damage.<br>&gt; Beat each floor's boss. Slay the dragon to win.<br>&gt; Die? You keep everything.<br>&gt; Beat a world's boss, then step through the portal to a new world with new weapons.</div>
 <div id="hstat"></div>
</div></div>
<script>
const W0=[["Rusty Dagger",2],["Iron Sword",5],["Steel Axe",8],["Flame Blade",12],["Dragonbane",17]],WI0=["🔪","🗡️","🪓","🔥","🐲"];
const A0=[["Rags",0],["Leather Vest",2],["Chainmail",4],["Knight Plate",7],["Dragon Scale",10]],AI0=["👕","🦺","⛓️","🛡️","🐉"];
const W=[["Rusty Dagger",2,0,0,0,"🔪"],["Wooden Club",3,0,0,0,"🏏"],["Iron Sword",5,1,0,0,"🗡️"],["Hunter Bow",4,1,.3,0,"🏹"],["Steel Axe",8,2,0,0,"🪓"],["War Hammer",9,2,0,0,"🔨"],["Fang Dagger",6,2,0,.25,"🦷"],["Flame Blade",12,3,0,0,"🔥"],["Thunder Spear",11,3,.25,0,"🔱"],["Blood Reaver",10,3,0,.3,"🩸"],["Dragonbane",17,4,0,0,"🐲"],["Storm Bow",14,4,.4,0,"⚡"]];
const A=[["Rags",0,0,0,"👕"],["Torn Cloak",1,0,0,"🧥"],["Leather Vest",2,1,0,"🦺"],["Mage Robe",2,1,.15,"👘"],["Chainmail",4,2,0,"⛓️"],["Shadow Cloak",3,2,.25,"🥷"],["Knight Plate",7,3,0,"🛡️"],["Elven Mail",5,3,.2,"🧝"],["Dragon Scale",10,4,0,"🐉"],["Storm Plate",8,4,.15,"🌩️"]];
W.push(["Frostbrand",20,5,0,0,"❄️"],["Glacier Maul",23,5,0,0,"🧊"],["Wolf Fang",18,5,0,.3,"🐺"],["Magma Cleaver",28,6,0,0,"🌋"],["Meteor Hammer",32,6,0,0,"☄️"],["Phoenix Talon",24,6,0,.3,"🦅"],["Void Blade",38,7,0,0,"🌌"],["Soul Reaper",34,7,0,.35,"☠️"],["Star Bow",30,7,.45,0,"🌠"]);
A.push(["Yeti Hide",12,5,0,"🦣"],["Snow Cloak",9,5,.25,"⛄"],["Frost Mail",11,5,.1,"🏔️"],["Obsidian Plate",18,6,0,"🌑"],["Lava Scale",15,6,.12,"🦎"],["Ember Robe",13,6,.3,"🧙"],["Void Plate",23,7,0,"🪐"],["Shade Robe",17,7,.35,"👁️"],["Cosmic Mail",20,7,.15,"🌟"]);
W.push(['Frying Pan',3,0,0,0,'🍳'],['Bone Club',6,1,0,0,'🦴'],['Pickaxe',9,2,0,0,'⛏️'],['Moon Blade',12,3,.2,0,'🌙'],['Serpent Fang',11,3,0,.25,'🐍'],['Crystal Staff',16,4,.3,0,'💎'],['Excalibur',18,4,0,.15,'✨'],['Blizzard Rod',21,5,.2,0,'🌨️'],['Sun Spear',30,6,.25,0,'☀️'],['Nova Edge',36,7,.3,0,'💫']);
const RW0=W.length;
W.push(["Goblin King's Mace",7,1,0,0,'⚒️'],['Lich Scepter',11,2,.15,0,'🪄'],['Dragonfang',15,3,0,.1,'🐉'],["Giant's Icicle",21,5,0,0,'🏔️'],['Mammoth Tusk',24,5,0,.15,'🐘'],["Queen's Scepter",26,5,.3,0,'👑'],['Rex Jawbone',29,6,0,.2,'🦖'],['Forge Anvil',33,6,0,0,'⚙️'],['Wyrmfire Bomb',36,6,.2,0,'🧨'],['Rift Orb',40,7,.25,0,'🔮'],['Night Scythe',44,7,0,.35,'🦇'],['Chaos Spiral',48,7,.35,0,'🌀'],['Thunder Hammer',52,8,.3,0,'🌩️'],['Solar Lance',56,8,0,.2,'🌞'],['Staff of Creation',62,8,.2,.25,'🪐']);
W.push(["Poseidon's Wrath",50,8,0,.2,'🌊'],["Apollo's Bow",46,8,.5,0,'🏹'],['Artemis Starbow',48,8,.45,.1,'🌠'],['Hades Reaper',58,8,0,.35,'💀'],["Athena's Aegis",57,8,.25,0,'🏛️'],['Ares Warblade',60,8,.3,0,'⚔️']);
A.push(['Aegis Plate',30,8,0,'🏛️'],['Divine Robe',22,8,.35,'👼'],['Titan Mail',26,8,.15,'🗿']);
W.push(['Skeleton Key Blade',10,2,.1,0,'🗝️'],['Iron Fist',13,3,0,.1,'🥊'],["Witch's Broom",16,4,.2,0,'🧹'],['Star Lance',17,4,0,.2,'🔭'],['Frost Fishing Rod',19,5,.25,0,'🎣'],['Ice Flail',22,5,0,.2,'🎳'],['Glacial Anchor',25,5,0,0,'⚓'],['Magma Magnet',27,6,.2,0,'🧲'],['Lava Stick',31,6,.15,0,'🏑'],['Forgemaster Tools',34,6,0,.25,'🛠️'],['Chain of Souls',39,7,0,.3,'🔗'],['Cosmic Dart',35,7,.4,0,'🎯'],['Black Hole Staff',41,7,.2,.2,'🕳️'],['Trident of Olympus',55,8,.25,.1,'🔱'],['Zeus Thunderbolt',53,8,.4,.1,'⚡']);
const WI=W.map(x=>x[5]),AI=A.map(x=>x[4]);
const RN=["Common","Uncommon","Rare","Epic","Legendary","Mythic","Divine","Cosmic","Godly"];
const F=[
 {n:"The Rat Cellar",m:[["🐀","Giant Rat",14,4],["👺","Goblin",20,5],["💀","Skeleton",26,6]],b:["👑","Goblin King",55,9]},
 {n:"The Bone Halls",m:[["👹","Orc",40,9],["👻","Wraith",38,11],["🧌","Ogre",55,11]],b:["🧙","The Lich",100,15]},
 {n:"The Dragon's Lair",m:[["🧟","Cave Troll",75,14],["😈","Demon",70,16],["🗿","Stone Golem",90,15]],b:["🐉","Ancient Dragon",150,18]}];
const r=(a,b)=>a+Math.floor(Math.random()*(b-a+1)),$=id=>document.getElementById(id),wait=ms=>new Promise(f=>setTimeout(f,ms));
const SC={};
function E(e,s){const k=e+s;if(!SC[k]){const n=s>=96?24:s>=64?18:14,c=document.createElement("canvas");c.width=c.height=n;const x=c.getContext("2d");x.font=(n*.8)+'px "Apple Color Emoji","Segoe UI Emoji","Noto Color Emoji",sans-serif';x.textAlign="center";x.textBaseline="middle";x.fillText(e,n/2,n/2+1);const d=x.getImageData(0,0,n,n),p=d.data;for(let i=0;i<p.length;i+=4){p[i+3]=p[i+3]>100?255:0;for(let j=0;j<3;j++)p[i+j]=Math.round(p[i+j]/64)*64}x.putImageData(d,0,0);SC[k]=c.toDataURL()}return `<img class="px" src="${SC[k]}" width="${s}" height="${s}" alt="">`}
let g,mon,busy;
function ov(h){$("ovc").innerHTML=h;const b=$("ovc").querySelector(".big");if(b)b.innerHTML=(b.textContent.match(/\p{Extended_Pictographic}\uFE0F?/gu)||[]).map(x=>E(x,96)).join("");$("ov").classList.remove("hide")}
function title(){ov(`<div class="big">⚔️🐉</div><h2>DEPTHS OF DOOM</h2><p>Slay monsters, loot better weapons and armour, and topple the boss of each floor. Three floors. One dragon.</p><button onclick="start()">ENTER THE DUNGEON</button>`)}
let live=null;
function save(){live=JSON.stringify(g);try{localStorage.setItem("dod",live)}catch(e){}}
function load(){let s=live;try{s=localStorage.getItem("dod")||s}catch(e){}try{return s?JSON.parse(s):null}catch(e){return null}}
function clearSave(){live=null;try{localStorage.removeItem("dod")}catch(e){}}
function home(){busy=true;const s=load();$("hCont").disabled=!s;$("hFuse").disabled=!s;$("hstat").textContent=s?`SAVED: FLOOR ${s.f+1} - LV ${s.lv}`:"NO SAVED RUN YET";$("hsp").innerHTML=`<div>${heroHTML()}</div><div>${SP(MS.Orc[0],MS.Orc[1].split(' '),MS.Orc[2],72)}</div><div>${SP('D',BS['Ancient Dragon'].p,[],108)}</div>`;$("help").classList.add("hide");$("ov").classList.add("hide");$("home").classList.remove("hide")}
function newGame(){clearSave();start()}
function cont(){const s=load();if(!s)return;g=s;if(!g.iw){g.iw=[0];g.ia=[0];g.w=0;g.a=0}g.nw=g.nw||0;if(g.hp<=0)g.hp=g.max;$("home").classList.add("hide");$("ov").classList.add("hide");$("log").innerHTML="";log("Welcome back, hero.");busy=false;spawn()}
function retry(){g.hp=g.max;g.k=0;$("ov").classList.add("hide");log("You wake at the start of the floor with all your gear and levels.");busy=false;spawn()}
function start(){g={f:0,k:0,hp:60,max:60,lv:1,xp:0,pot:3,w:0,a:0,iw:[0],ia:[0],nw:0};$("ov").classList.add("hide");$("home").classList.add("hide");$("log").innerHTML="";log("You descend into the dungeon...");busy=false;spawn()}
function log(t){const p=document.createElement("p");p.textContent=t;$("log").appendChild(p);$("log").scrollTop=1e9}
function spawn(){
 const d=g.k>=3?F[g.f].b:F[g.f].m[g.k];
 mon={e:d[0],n:d[1],hp:d[2],max:d[2],atk:d[3],boss:g.k>=3};
 $("mon").className=mon.boss?"boss":"";$("mon").style.display="";busy=false;save();entry();
 log(mon.boss?`⚠ BOSS: the ${mon.n} blocks your path!`:`A ${mon.n} appears!`);ui()}
function ui(){
 const nI=Math.max(0,(g.iw||[]).length+(g.ia||[]).length-2);$("bagb").disabled=busy;$("bagb").textContent=`BAG - ${nI} ITEMS${g.nw?" - "+g.nw+" NEW!":""}`;$("me").innerHTML=mon.boss&&BS[mon.n]?SP(BS[mon.n].t,BS[mon.n].p,BS[mon.n].x,BS[mon.n].s||144):MS[mon.n]?SP(MS[mon.n][0],MS[mon.n][1].split(' '),MS[mon.n][2],108):E(mon.e,120);$("hero").innerHTML=heroHTML();document.querySelectorAll(".torch").forEach(t=>t.innerHTML=E("🔥",56));$("mn").textContent=mon.n;
 $("mb").style.width=Math.max(0,mon.hp/mon.max*100)+"%";$("mt").textContent=Math.max(0,mon.hp)+" / "+mon.max;
 $("pb").style.width=g.hp/g.max*100+"%";$("pt").textContent=g.hp+" / "+g.max;
 $("lv").textContent=g.lv;theme(Math.floor(g.f/3));$("fn").textContent=`World ${Math.floor(g.f/3)+1} - Level ${g.f%3+1} · ${F[g.f].n}`;$("xb").style.width=(g.xp%100)+"%";
 let p="";for(let f=0;f<3;f++){for(let k=0;k<4;k++){const gf=Math.floor(g.f/3)*3+f,done=gf<g.f||(gf==g.f&&k<g.k),cur=gf==g.f&&k==g.k;p+=`<i class="${k==3?"b ":""}${done?"d":cur?"c":""}"></i>`}if(f<2)p+="<span>›</span>"}
 $("pips").innerHTML=p;
 $("slots").innerHTML=`<div class="slot" style="--c:var(--t${W[g.w][2]})"><small>Weapon</small><b>${WE(g.w,52)}</b><span>${W[g.w][0]}</span><em>+${W[g.w][1]} attack</em></div>
 <div class="slot" style="--c:var(--t${A[g.a][2]})"><small>Armour</small><b>${AE(g.a,52)}</b><span>${A[g.a][0]}</span><em>−${A[g.a][1]} damage</em></div>
 <div class="slot"><small>Potions</small><b>${E("🧪",42)}</b><span>×${g.pot}</span><em>heal 40</em></div>`;
 const B=[["a","⚔️","Attack","normal"],["h","💥","Heavy","60% · ×1.8"],["d","🛡️","Guard","half damage"],["p","🧪","Potion","+40 HP"]];
 $("btns").innerHTML=B.map(x=>`<button data-k="${x[0]}" ${busy||(x[0]=="p"&&(g.pot<1||g.hp>=g.max))?"disabled":""}><b>${E(x[1],28)}</b><span>${x[2]}</span><small>${x[3]}</small></button>`).join("");
 document.querySelectorAll("#btns button").forEach(b=>b.onclick=()=>act(b.dataset.k))}
function fx(el,c,ms=400){el.classList.remove(c);void el.offsetWidth;el.classList.add(c);setTimeout(()=>el.classList.remove(c),ms)}
function num(t,col,x,y){const d=document.createElement("div");d.className="fl";d.textContent=t.replace("\u{1F4A5}","!");d.style.color=col;d.style.left=x+"px";d.style.top=y+"px";$("stage").appendChild(d);setTimeout(()=>d.remove(),1000)}
function toast(t,t_){const e=$("toast");e.innerHTML=t;e.style.setProperty("--c",`var(--t${t_})`);e.classList.add("on");setTimeout(()=>e.classList.remove("on"),2400)}
[["Frost Gate",["🥶","Ice Imp"],["🐺","Frost Wolf"],["⛄","Snow Golem"],["🧊","Frost Giant"]],
["Glacier Deep",["🐻","Ice Bear"],["🧛","Frost Vampire"],["🦅","Blizzard Hawk"],["🦣","Ancient Mammoth"]],
["Crystal Throne",["🧊","Ice Elemental"],["👻","Frost Ghost"],["🥶","Frozen Knight"],["👸","Ice Queen"]],
["Ash Fields",["🦂","Fire Scorpion"],["🐍","Lava Snake"],["🔥","Ember Sprite"],["🦖","Magma Rex"]],
["Magma Tunnels",["🦎","Lava Lizard"],["👹","Fire Ogre"],["🗿","Magma Golem"],["👿","Forge Lord"]],
["Inferno Core",["💀","Cinder Skeleton"],["🦍","Fire Giant"],["🦅","Phoenix"],["🐲","Inferno Wyrm"]],
["Star Rift",["👁️","Watcher"],["🛸","Void Saucer"],["👽","Alien Stalker"],["🦑","Void Kraken"]],
["Shadow Spires",["🦇","Night Bat"],["🕷️","Shade Spider"],["👤","Shadow Wraith"],["☠️","The Reaper"]],
["Eternal Throne",["🐙","Tentacle Horror"],["👾","Chaos Beast"],["🌀","Rift Spawn"],["🐉","Eternal Dragon"]]].forEach((x,i)=>{const L=i+3,s=1+(L-3)*.24,wb=L%3==2;F.push({n:x[0],m:[1,2,3].map(j=>[x[j][0],x[j][1],Math.round((80+j*10)*s),Math.round(16+j+(L-3)*2.2)]),b:[x[4][0],x[4][1],Math.round((170+(wb?60:0))*s),Math.round(20+(L-3)*2.2+(wb?3:0))]})});
const WD=[{n:"The Dungeon",c:["#cfae82","#a58258","#8a6a48","#ffd84a"]},{n:"Frozen Caverns",c:["#d4eefb","#9fcfe8","#7fb0cc","#5ff3ff"]},{n:"Volcano Forge",c:["#e0976a","#b8613a","#8a4528","#ff8a3a"]},{n:"The Void",c:["#8878c0","#6a58a8","#4b3c88","#e07dff"]}];
function theme(w){const c=WD[w].c,s=document.documentElement.style;s.setProperty("--wl",c[0]);s.setProperty("--wm",c[1]);s.setProperty("--wf",c[2])}
function tierN(f){const w=Math.floor(f/3),fi=f%3;if(!w)return Math.min(4,fi+r(0,1)+(fi==2&&Math.random()<.2?1:0));const T=4+w;return Math.random()<.35+fi*.2?T:T-1}
function tierB(f){const w=Math.floor(f/3);return w?4+w:f+1}
async function portal(){busy=true;const nw=Math.floor(g.f/3)+1,p=$("ptl");p.style.setProperty("--pc",WD[nw].c[3]);$("ph").innerHTML=heroHTML();$("ptt").textContent="ENTERING WORLD "+(nw+1);$("ptw").textContent=WD[nw].n.toUpperCase();log(`A portal opens! Stepping into ${WD[nw].n}...`);p.classList.remove("hide","on");void p.offsetWidth;p.classList.add("on");await wait(2450);theme(nw);g.hp=g.max;await wait(1400);p.classList.add("hide");p.classList.remove("on")}
let crit=false;const dmg=()=>{const d=3+W[g.w][1]+r(0,3);crit=Math.random()<W[g.w][3];return crit?d*2:d};
const BA={"Goblin King":["slam"],"Frost Giant":["slam"],"Forge Lord":["slam"],"Ancient Mammoth":["charge"],"Magma Rex":["charge"],"The Reaper":["charge"],"The Lich":["shoot","🔮",1,56],"Ice Queen":["shoot","❄️",3,40],"Void Kraken":["shoot","🌀",2,48],"Ancient Dragon":["shoot","🔥",5,44],"Inferno Wyrm":["shoot","🔥",5,44],"Eternal Dragon":["shoot","🌌",5,44]},RG=["🏹","⚡","🌠"];
const cc=el=>{const s=$("stage").getBoundingClientRect(),r=el.getBoundingClientRect();return[r.left-s.left+r.width/2,r.top-s.top+r.height/2]};
function mk(html,x,y,w){const d=document.createElement("div");d.style.cssText=`position:absolute;z-index:7;pointer-events:none;left:${x-w/2}px;top:${y-w/2}px;width:${w}px;height:${w}px`;d.innerHTML=html;$("stage").appendChild(d);return d}
const go=(d,k,ms)=>{d.animate(k,{duration:ms,easing:"steps(6)"}).onfinish=()=>d.remove()};
function fly(html,a,b,ms,w){const d=mk(html,a[0],a[1],w);go(d,[{transform:"translate(0,0)"},{transform:`translate(${b[0]-a[0]}px,${b[1]-a[1]}px)`}],ms);return wait(ms)}
function boom(p,col,n,dist){for(let i=0;i<n;i++){const d=mk("",p[0],p[1],8),a=i/n*6.283;d.style.background=col;d.style.border="2px solid #000";go(d,[{transform:"translate(0,0)",opacity:1},{transform:`translate(${Math.cos(a)*dist}px,${Math.sin(a)*dist}px)`,opacity:0}],420)}}
function ring(p,col){const d=mk("",p[0],p[1],40);d.style.border="6px solid "+col;go(d,[{transform:"scale(.3)",opacity:1},{transform:"scale(4)",opacity:0}],500)}
function slash(p,big){(big?[45,-45]:[45]).forEach((a,i)=>{const d=mk("",p[0],p[1],big?150:100);d.style.height="12px";d.style.top=(p[1]-6)+"px";d.style.background="#fff";d.style.border="3px solid #000";d.style.boxShadow="0 0 0 3px "+(i?"#ffb830":"#ff7a3a");go(d,[{transform:`rotate(${a}deg) scaleX(0)`,opacity:1},{transform:`rotate(${a}deg) scaleX(1)`,opacity:1,offset:.4},{transform:`rotate(${a}deg) scaleX(1)`,opacity:0}],380+i*80)})}
function hitFx(t){const m=cc($("me")),wp=W[g.w];if(RG.includes(wp[5])){ring(m,`var(--t${wp[2]})`);boom(m,"#fff",8,50)}else{slash(m,t=="h");boom(m,"#ffe27a",t=="h"?12:7,t=="h"?70:45)}}
const TP={H:['....5.55','...55555','...11111','...11411','...11111','....2222','..333333','.3333333','.3.33333','.3.33333','.1.32222','...33333','...3333.','...3333.','...2222.','..22222.'],
D:['....5.5.','...11111','...11111','...11411','..111111','...11333','.2.11111','22.11333','222.1333','2222.333','.222.333','..2.1333','....1333','...11333','...11.11','..111.11'],
B:['..5.....','.5511111','..111111','.1111411','.1111111','.1112222','.1122222','.1133333','11111111','11111111','11311311','11111111','11111111','.111.111','.222.222','.222.222'],
K:['.....111','...11111','..111111','.1111111','.1141111','.1111111','.1112111','..111111','.1.1.1.1','.1.1.1.1','1.1.1.1.','1.1.1.1.','.1.1.1.1','.1.1.1.1','1.1.1.1.','.1...1..']},SPC={};
function SP(tp,pal,ex,s){const k=tp+pal+JSON.stringify(ex)+s;if(!SPC[k]){const G=Array.from({length:18},()=>Array(18).fill(null));TP[tp].forEach((row,y)=>{for(let x=0;x<8;x++){const c=row[x];if(c!='.')G[y+1][x+1]=G[y+1][16-x]=pal[+c-1]}});ex.forEach(([x,y,w,h,c])=>{for(let j=y;j<y+h;j++)for(let i=x;i<x+w;i++)if(j>=0&&j<16&&i>=0&&i<16)G[j+1][i+1]=c});
 const cv=document.createElement('canvas');cv.width=cv.height=18;const q=cv.getContext('2d');
 for(let y=0;y<18;y++)for(let x=0;x<18;x++){if(G[y][x]){q.fillStyle=G[y][x];q.fillRect(x,y,1,1)}else if([[1,0],[-1,0],[0,1],[0,-1]].some(([a,b])=>G[y+b]&&G[y+b][x+a])){q.fillStyle='#000';q.fillRect(x,y,1,1)}}
 SPC[k]=cv.toDataURL()}return `<img class="px" src="${SPC[k]}" width="${s}" height="${s}" alt="">`}
const BS={
'Goblin King':{t:'H',p:['#6bbf3a','#3f7a22','#8a5a2b','#ff3b2f','#ffd84a'],x:[[14,4,1,10,'#7a4a1c'],[13,2,3,3,'#ff3b2f'],[1,3,2,2,'#6bbf3a']]},
'The Lich':{t:'H',p:['#eee8d0','#a79bd0','#5b2e91','#59ff8a','#3a1a66'],x:[[14,1,1,14,'#6b4a2a'],[13,0,3,3,'#59ff8a']]},
'Frost Giant':{t:'H',p:['#bfe0f5','#6fa8cc','#4a8fc9','#1b2a6b','#ffffff'],x:[[4,5,8,3,'#ffffff'],[14,3,2,11,'#9fcfe8'],[1,3,2,3,'#ffffff']]},
'Ice Queen':{t:'H',p:['#f6e6ee','#8ec9e8','#9fe0ff','#2a6fd6','#e8fbff'],x:[[2,2,2,9,'#e8fbff'],[12,2,2,9,'#e8fbff'],[14,5,1,8,'#bfe9ff'],[13,3,3,3,'#ffffff']]},
'Forge Lord':{t:'H',p:['#b8321f','#6a1a10','#2e2a33','#ffe94a','#ff7a2a'],x:[[2,0,2,4,'#ff7a2a'],[12,0,2,4,'#ff7a2a'],[12,4,4,3,'#8a8f98'],[14,7,1,7,'#6b4a2a']]},
'The Reaper':{t:'H',p:['#14101c','#2a2433','#1c1626','#ff3030','#14101c'],x:[[14,1,1,14,'#6b4a2a'],[8,0,7,2,'#d6dde2'],[8,2,2,2,'#d6dde2']]},
'Ancient Dragon':{t:'D',p:['#4caf50','#2e7d32','#e0cf7a','#ffeb3b','#f5f0d0'],x:[]},
'Inferno Wyrm':{t:'D',p:['#d9402b','#7a1f10','#ffb347','#ffffff','#2a1a10'],x:[[6,0,4,2,'#ffd84a']]},
'Eternal Dragon':{t:'D',p:['#5a3aa8','#2a1860','#ffd84a','#ff5df0','#ffd84a'],x:[[3,0,10,1,'#ffd84a'],[7,14,2,2,'#ffd84a']]},
'Ancient Mammoth':{t:'B',p:['#8a5a3b','#5a3a24','#6f4630','#111111','#6f4630'],x:[[7,6,2,8,'#8a5a3b'],[3,8,1,6,'#fff8e0'],[12,8,1,6,'#fff8e0']]},
'Magma Rex':{t:'B',p:['#c0392b','#7a1f10','#ff8a3a','#ffe94a','#ffb830'],x:[[3,0,2,2,'#ffb830'],[11,0,2,2,'#ffb830'],[7,0,2,1,'#ffb830'],[4,7,8,1,'#ffffff']]},
'Void Kraken':{t:'K',p:['#7a4aa8','#4a2b73','#b48cff','#ffe94a','#7a4aa8'],x:[[3,4,2,2,'#ffffff'],[11,4,2,2,'#ffffff'],[4,5,1,1,'#111111'],[11,5,1,1,'#111111'],[7,1,2,2,'#b48cff']]}};
const AC={'Rags':'#8a7a5a','Torn Cloak':'#7a6a8a','Leather Vest':'#a0693a','Mage Robe':'#6a4fc0','Chainmail':'#aab2bb','Shadow Cloak':'#3e3e52','Knight Plate':'#e3e9f0','Elven Mail':'#4caf6a','Dragon Scale':'#d9402b','Storm Plate':'#4aa3ff','Yeti Hide':'#eef4f8','Snow Cloak':'#bfe9ff','Frost Mail':'#7fd4f2','Obsidian Plate':'#40343f','Lava Scale':'#e0602a','Ember Robe':'#ff8a3a','Void Plate':'#6a3fc0','Shade Robe':'#2c2260','Cosmic Mail':'#ffd84a'};
const dk=(h,f)=>'#'+[1,3,5].map(i=>Math.round(parseInt(h.substr(i,2),16)*f).toString(16).padStart(2,'0')).join('');
function heroHTML(){const a=A[g.a],m=AC[a[0]]||'#999',pal=['#f1c27d',dk(m,.6),m,'#222',a[2]>=2?m:'#6b4423'];
 return `<div style="position:relative;width:72px;height:72px">${SP('H',pal,a[2]>=3?[[7,0,2,2,'#ff4040']]:[],72)}<div style="position:absolute;right:-30px;top:8px;transform:rotate(25deg)">${WE(g.w,60)}</div></div>`}
async function atkAnim(t){
 const h=$("hero"),hc=cc(h),mc=cc($("me")),wp=W[g.w],hv=t=="h";
 if(RG.includes(wp[5])){
  h.animate([{transform:"translate(0,0)"},{transform:"translate(-14px,0)"},{transform:"translate(0,0)"}],{duration:300,easing:"steps(4)"});
  await wait(150);const a=Math.atan2(mc[1]-hc[1],mc[0]-hc[0]),ps=[];
  for(let i=0;i<(hv?3:1);i++){ps.push(fly(`<div style="width:44px;height:8px;margin-top:16px;background:var(--t${wp[2]});border:3px solid #000;transform:rotate(${a}rad)"></div>`,[hc[0]+20,hc[1]-10+i*10],[mc[0],mc[1]+i*8-8],320,44));await wait(110)}
  await Promise.all(ps);return}
 const dx=(mc[0]-hc[0])*.8,dy=(mc[1]-hc[1])*.8-(hv?30:0),ms=hv?650:480;
 h.animate([{transform:"translate(0,0)",offset:0},{transform:`translate(${dx}px,${dy}px)`,offset:.45},{transform:`translate(${dx}px,${dy}px)`,offset:.6},{transform:"translate(0,0)",offset:1}],{duration:ms,easing:"steps(7)"});
 await wait(ms*.45);
 const z=hv?84:64,s=mk(WE(g.w,z),mc[0]-50,mc[1]-30,z);go(s,[{transform:"rotate(-110deg)"},{transform:"rotate(70deg)"}],280)}
async function monAtk(){
 const el=$("mon"),hc=cc($("hero")),mc=cc($("me")),dx=hc[0]-mc[0],dy=hc[1]-mc[1],T=mon.boss?(BA[mon.n]||["slam"]):["bite"];
 const mv=(k,ms)=>el.animate(k.map(q=>({transform:`translateX(-50%) translate(${q[0]}px,${q[1]}px) scale(${q[2]})`,offset:q[3]})),{duration:ms,easing:"steps(6)"});
 if(T[0]=="bite"){mv([[0,0,1,0],[dx*.7,dy*.7,1.1,.4],[0,0,1,1]],450);await wait(190)}
 else if(T[0]=="slam"){mv([[0,0,1,0],[dx*.2,-70,1.1,.3],[dx*.55,dy*.55,1.2,.5],[dx*.55,dy*.55,1.2,.62],[0,0,1,1]],900);await wait(460);ring([mc[0]+dx*.55,mc[1]+dy*.55],"#fff");boom(hc,"#ff9a3a",10,60);await wait(80)}
 else if(T[0]=="charge"){mv([[0,0,1,0],[-dx*.12,-dy*.12,1,.3],[dx*.9,dy*.9,1.15,.55],[dx*.9,dy*.9,1.15,.65],[0,0,1,1]],850);await wait(470);boom(hc,"#fff",10,60)}
 else{mv([[0,0,1,0],[0,-8,1.18,.5],[0,0,1,1]],450);await wait(300);const ps=[];
  for(let i=0;i<T[2];i++){ps.push(fly(E(T[1],T[3]),mc,[hc[0]+i%2*10,hc[1]+i*8-8],420,T[3]));await wait(110)}
  await Promise.all(ps);boom(hc,"#ffb347",10,60)}}
WD.push({n:"Gods' World",c:['#fff2c8','#e8c878','#c9a24a','#fff6a0']});
[['Olympus Gate',['🦅','Harpy'],['🐎','Spectral Steed'],['🗿','Marble Titan'],['⚡','Storm Titan']],['Sun Temple',['🦁','Sun Lion'],['🐂','Bronze Bull'],['👁️','Oracle Eye'],['🌞','Helios']],['Throne of Gods',['😇','Fallen Angel'],['🛡️','Divine Guardian'],['⚖️','Judgement'],['👑','The Allfather']]].forEach((x,i)=>{const L=i+12,s=1+(L-3)*.24,wb=L%3==2;F.push({n:x[0],m:[1,2,3].map(j=>[x[j][0],x[j][1],Math.round((80+j*10)*s),Math.round(16+j+(L-3)*2.2)]),b:[x[4][0],x[4][1],Math.round((170+(wb?60:0))*s),Math.round(20+(L-3)*2.2+(wb?3:0))]})});
Object.assign(BS,{'Storm Titan':{t:'H',p:['#8fb7ff','#3a5fb0','#2a3f8f','#ffe94a','#ffe94a'],x:[[13,3,3,2,'#ffe94a'],[12,5,3,2,'#ffe94a'],[13,7,3,2,'#ffe94a']]},'Helios':{t:'H',p:['#ffd9a0','#c98a2a','#f0b030','#ff5a1a','#ffd84a'],x:[[2,0,12,1,'#fff6a0'],[0,6,2,1,'#ffd84a'],[14,6,2,1,'#ffd84a'],[0,9,2,1,'#ffd84a'],[14,9,2,1,'#ffd84a'],[14,2,1,12,'#fff6a0']]},'The Allfather':{t:'H',p:['#f2eadf','#8a7bb8','#ffffff','#7a4aff','#ffd84a'],x:[[0,6,3,5,'#ffffff'],[13,6,3,5,'#ffffff'],[14,0,1,15,'#ffd84a'],[13,0,3,2,'#c58bff'],[5,5,6,2,'#ffffff']]}});
Object.assign(AC,{'Aegis Plate':'#fff2b0','Divine Robe':'#f4e6ff','Titan Mail':'#9fb4ff'});
const DUST='<div style="width:24px;height:24px;background:#f3e6bd;border:3px solid #000"></div>';
const NA=[[['claw'],['shoot','🗡️',1,36,'arc'],['chomp']],[['shoot','❄️',2,32,'line'],['chomp'],['shoot','🧊',1,40,'arc']],[['shoot','🔥',2,36,'wave'],['claw'],['shoot','☄️',2,36,'rain']],[['shoot','🔮',2,36,'line'],['shoot','👁️',1,40,'wave'],['claw']],[['bolt'],['shoot','☀️',2,36,'fan'],['shoot','✨',3,32,'rain']]];
const BB={'Goblin King':['quake'],'The Lich':['shoot','💀',3,40,'wave'],'Ancient Dragon':['shoot','🔥',5,44,'line'],'Frost Giant':['shoot','🧊',4,40,'rain'],'Ancient Mammoth':['charge'],'Ice Queen':['shoot','❄️',5,36,'fan'],'Magma Rex':['shoot','☄️',3,44,'arc'],'Forge Lord':['shoot','🔨',1,64,'spin'],'Inferno Wyrm':['shoot','🔥',6,40,'rain'],'Void Kraken':['nova','#b48cff'],'The Reaper':['blink'],'Eternal Dragon':['beam','#ff5df0'],'Storm Titan':['bolt'],'Helios':['multi',[['nova','#ffe14a'],['shoot','☀️',3,56,'arc']]],'The Allfather':['multi',[['nova','#ffffff'],['bolt'],['beam','#c58bff']]]};
function fly(html,a,b,ms,w,st,i,n){const d=mk(html,a[0],a[1],w),X=b[0]-a[0],Y=b[1]-a[1],P=(x,y,r)=>({transform:`translate(${x}px,${y}px) rotate(${r||0}deg)`});go(d,st=='arc'?[P(0,0),P(X/2,Y/2-90,360),P(X,Y,720)]:st=='wave'?[P(0,0),P(X*.25,Y*.25-30),P(X*.5,Y*.5+30),P(X*.75,Y*.75-30),P(X,Y)]:st=='fan'?[P(0,0),P(X*.4,Y*.4+(i-(n-1)/2)*60),P(X,Y)]:[P(0,0),P(X,Y,st=='spin'?720:0)],ms);return wait(ms)}
function ring(p,col,sc){const d=mk('',p[0],p[1],40);d.style.border='6px solid '+col;go(d,[{transform:'scale(.3)',opacity:1},{transform:`scale(${sc||4})`,opacity:0}],500)}
function beam(a,b,col,h){const L=Math.hypot(b[0]-a[0],b[1]-a[1]),r=Math.atan2(b[1]-a[1],b[0]-a[0]),d=document.createElement('div');d.style.cssText=`position:absolute;z-index:7;pointer-events:none;left:${a[0]}px;top:${a[1]-h/2}px;width:${L}px;height:${h}px;background:${col};border:4px solid #fff;box-shadow:0 0 0 4px #000;transform-origin:0 50%`;$('stage').appendChild(d);d.animate([{transform:`rotate(${r}rad) scaleX(0)`,opacity:1},{transform:`rotate(${r}rad) scaleX(1)`,opacity:1,offset:.3},{transform:`rotate(${r}rad) scaleX(1)`,opacity:1,offset:.8},{transform:`rotate(${r}rad) scaleX(1)`,opacity:0}],{duration:900,easing:'steps(8)'}).onfinish=()=>d.remove()}
function bolt(p){const d=mk('',p[0],0,40);d.style.height=(p[1]+16)+'px';d.style.top='0px';d.style.background='#fff27a';d.style.clipPath='polygon(45% 0,100% 0,55% 35%,90% 35%,15% 100%,40% 55%,0 55%)';go(d,[{opacity:1},{opacity:0,offset:.3},{opacity:1,offset:.5},{opacity:0}],450)}
function claw(p){[-16,0,16].forEach(o=>{const d=mk('',p[0]+o,p[1],70);d.style.height='8px';d.style.top=(p[1]-4)+'px';d.style.background='#ff4a3a';d.style.border='2px solid #000';go(d,[{transform:'rotate(60deg) scaleX(0)',opacity:1},{transform:'rotate(60deg) scaleX(1)',opacity:1,offset:.4},{transform:'rotate(60deg) scaleX(1)',opacity:0}],380)})}
function jaws(p){[-1,1].forEach(s=>{const d=mk('',p[0],p[1]+s*34,56);d.style.height='14px';d.style.top=(p[1]+s*34-7)+'px';d.style.background='repeating-linear-gradient(90deg,#fff 0 8px,#bbb 8px 12px)';d.style.border='3px solid #000';go(d,[{transform:'translateY(0)'},{transform:`translateY(${-s*26}px)`,offset:.5},{transform:`translateY(${-s*26}px)`,opacity:0}],450)})}
function giveW(id){const it=W[id];if(g.iw.includes(id)){log(`The ${mon.n} drops ${it[0]}, but you already own it.`);return}g.iw.push(id);g.nw=(g.nw||0)+1;toast(`${E(it[5],28)} ${it[0]}<br>${RN[it[2]]}! Boss weapon`,it[2]);log(`★ BOSS WEAPON: ${it[0]} (${RN[it[2]]}). Added to bag!`)}
async function doAtk(T){
 const el=$('mon'),hc=cc($('hero')),mc=cc($('me')),dx=hc[0]-mc[0],dy=hc[1]-mc[1],k=T[0];
 const mv=(a,ms)=>el.animate(a.map(q=>({transform:`translateX(-50%) translate(${q[0]}px,${q[1]}px) scale(${q[2]})`,offset:q[3],opacity:q[4]==null?1:q[4]})),{duration:ms,easing:'steps(6)'});
 const pulse=()=>{mv([[0,0,1,0],[0,-8,1.18,.5],[0,0,1,1]],450);return wait(300)};
 const lunge=()=>{mv([[0,0,1,0],[dx*.7,dy*.7,1.1,.4],[0,0,1,1]],450);return wait(190)};
 if(k=='claw'){await lunge();claw(hc)}
 else if(k=='chomp'){await lunge();jaws(hc)}
 else if(k=='quake'){mv([[0,0,1,0],[dx*.2,-70,1.1,.3],[dx*.2,0,1.2,.5],[dx*.2,0,1.2,.62],[0,0,1,1]],900);await wait(460);ring([mc[0]+dx*.2,mc[1]+60],'#fff');const ps=[];for(let i=0;i<5;i++){ps.push(fly(DUST,[mc[0]+dx*.2,hc[1]+24],[hc[0],hc[1]+24],420,24));await wait(70)}await Promise.all(ps);boom(hc,'#f3e6bd',10,55)}
 else if(k=='charge'){boom([mc[0],mc[1]+60],'#f3e6bd',6,30);mv([[0,0,1,0],[-dx*.12,-dy*.12,1,.3],[dx*.9,dy*.9,1.15,.55],[dx*.9,dy*.9,1.15,.65],[0,0,1,1]],850);await wait(470);boom(hc,'#fff',10,60)}
 else if(k=='shoot'){await pulse();const n=T[2],st=T[4],ps=[];for(let i=0;i<n;i++){const o=(i-(n-1)/2)*30,a=st=='rain'?[hc[0]+o,-20]:mc,b=st=='rain'?[hc[0]+o,hc[1]]:[hc[0]+i%2*10,hc[1]+i*8-8];ps.push(fly(E(T[1],T[3]),a,b,st=='rain'?380:420,T[3],st,i,n));await wait(110)}await Promise.all(ps);boom(hc,'#ffb347',10,60)}
 else if(k=='beam'){await pulse();beam(mc,hc,T[1],28);await wait(500);boom(hc,T[1],12,70)}
 else if(k=='nova'){await pulse();for(let i=0;i<3;i++){ring(mc,T[1],7);await wait(160)}await wait(200);boom(hc,T[1],12,70)}
 else if(k=='bolt'){await pulse();for(let i=0;i<3;i++){bolt([hc[0]+(i-1)*36,hc[1]]);await wait(180)}fx($('flash'),'on');boom(hc,'#fff27a',12,70);await wait(120)}
 else if(k=='blink'){el.animate([{transform:'translateX(-50%)',opacity:1},{transform:'translateX(-50%)',opacity:0,offset:.25},{transform:'translateX(-50%)',opacity:0,offset:.7},{transform:'translateX(-50%)',opacity:1}],{duration:900,easing:'steps(6)'});await wait(400);boom(mc,'#3a2a50',10,50);slash(hc,true);boom(hc,'#ff4040',10,60);await wait(250)}
 else if(k=='multi'){for(const a of T[1])await doAtk(a)}
 else await lunge()}
async function monAtk(){await doAtk(mon.boss?(BB[mon.n]||['quake']):NA[Math.floor(g.f/3)][(g.k+g.f)%3])}
function dropW(t){const ok=i=>!g.iw.includes(i)&&!(i>=RW0&&i<RW0+15);for(let d=0;d<9;d++)for(const tt of d?[t-d,t+d]:[t]){const c=W.map((x,i)=>i).filter(i=>W[i][2]==tt&&ok(i));if(c.length){giveW(c[r(0,c.length-1)],1);return}}log('You have collected every weapon!')}
function giveW(id,fight){const it=W[id];if(g.iw.includes(id)){log(`You already own ${it[0]}.`);return}g.iw.push(id);g.nw=(g.nw||0)+1;toast(`${WE(id,40)} ${it[0]}<br>${RN[it[2]]}! ${fight?'New weapon':'Boss weapon'}`,it[2]);log(`${fight?'⚔ Dropped':'★ BOSS WEAPON'}: ${it[0]} (${RN[it[2]]}). Added to bag!`)}
let tq=Promise.resolve();function toast(t,t_){tq=tq.then(async()=>{const e=$('toast');e.innerHTML=t;e.style.setProperty('--c',`var(--t${t_})`);e.classList.add('on');await wait(1500);e.classList.remove('on');await wait(350)})}
Object.assign(TP,{R:['........','........','........','..55....','..551111','..111111','..114111','..111111','..112222','.1111111','.1111111','.1131111','.1111111','.11.1111','.22.2222','.22.2222'],
G:['.....111','...11111','..111111','..111111','..114111','..111111','..113333','..111111','.1111111','.1111111','.1111111','.1111111','.1111111','.11.11.1','.1..1..1','........'],
W:['........','........','.....555','....1111','....1411','....1331','.2..1111','22.11111','222.1111','2222.111','.222.111','..2..111','.....111','.....1.1','....33.3','........'],
N:['........','.....111','....1111','....1411','....1111','.....3.3','....1111','..111111','.1122222','11111111','11222222','11111111','.1122222','..111111','...11111','........'],
O:['........','.....111','...11111','..111111','.1111333','.1113344','.1113344','.1111333','.1111111','..111111','...11111','.....111','....2.2.','...2.2.2','....2.2.','........'],
U:['........','........','........','.....111','....1111','...11441','..111111','.2222222','22222222','.3.3.3.3','..2.2.2.','........','........','........','........','........'],
S:['........','........','........','........','.....111','...11111','..114111','..111111','.1111111','1.111111','.1111111','1.111111','.1.11111','1..1.111','1...1.11','........']});
const MS={
'Giant Rat':['R','#987 #654 #fab #f33 #fab',[[15,9,1,4,'#fab']]],
'Goblin':['H','#7c3 #472 #864 #f22 #472',[[2,3,2,2,'#7c3'],[12,3,2,2,'#7c3'],[14,8,1,4,'#ccc']]],
'Skeleton':['H','#eed #999 #ddc #111 #eed',[[14,3,1,10,'#bbb'],[13,2,3,2,'#ddd']]],
'Orc':['H','#693 #352 #765 #fd3 #321',[[4,5,1,2,'#fff'],[11,5,1,2,'#fff'],[14,2,2,4,'#999'],[14,6,1,6,'#642']]],
'Wraith':['G','#668 #335 #99c #ff3 #668',[]],
'Ogre':['H','#ca7 #864 #975 #200 #542',[[13,3,3,6,'#642'],[3,9,10,2,'#ca7']]],
'Cave Troll':['B','#797 #464 #686 #111 #464',[[3,8,1,4,'#fff'],[12,8,1,4,'#fff'],[7,7,2,2,'#464']]],
'Demon':['D','#c24 #512 #fa3 #ff0 #222',[]],
'Stone Golem':['H','#999 #666 #888 #fa3 #666',[[3,6,3,2,'#4a4'],[9,9,3,2,'#4a4'],[1,6,2,5,'#777'],[13,6,2,5,'#777']]],
'Ice Imp':['R','#6cf #38a #fff #f33 #fff',[[15,9,1,4,'#6cf']]],
'Frost Wolf':['R','#ccd #889 #fff #3af #ccd',[[4,8,1,2,'#fff'],[11,8,1,2,'#fff'],[15,8,1,4,'#ccd']]],
'Snow Golem':['H','#fff #bcd #eef #222 #222',[[7,4,2,1,'#f82'],[0,7,2,1,'#642'],[14,7,2,1,'#642']]],
'Ice Bear':['B','#eef #9bd #ace #123 #eef',[[3,8,1,3,'#fff'],[12,8,1,3,'#fff']]],
'Frost Vampire':['H','#ede #417 #213 #f22 #102',[[3,6,10,1,'#c22'],[5,5,1,1,'#fff'],[10,5,1,1,'#fff']]],
'Blizzard Hawk':['W','#8cf #46a #fd5 #fff #cef',[]],
'Ice Elemental':['G','#4df #28c #9ef #fff #4df',[[3,0,2,3,'#9ef'],[11,0,2,3,'#9ef'],[7,0,2,2,'#9ef']]],
'Frost Ghost':['G','#cde #89b #fff #36f #cde',[]],
'Frozen Knight':['H','#8ab #456 #678 #5cf #9bc',[[0,6,3,5,'#9ab'],[14,3,1,9,'#cde']]],
'Fire Scorpion':['S','#d43 #821 #fa3 #ff0 #d43',[[12,2,3,3,'#fa3'],[14,0,2,3,'#fa3'],[0,7,3,2,'#d43'],[13,7,3,2,'#d43']]],
'Lava Snake':['N','#e52 #a31 #fc4 #ff0 #e52',[]],
'Ember Sprite':['G','#fa2 #d41 #ff6 #fff #ff4',[[6,0,4,2,'#ff4']]],
'Lava Lizard':['R','#d62 #812 #fd4 #ff0 #fc3',[[15,10,1,3,'#d62'],[4,3,1,1,'#fc3'],[11,3,1,1,'#fc3']]],
'Fire Ogre':['H','#e63 #a31 #832 #ff0 #f90',[[13,2,3,7,'#f90'],[13,0,2,2,'#ff4'],[3,5,10,2,'#f90']]],
'Magma Golem':['H','#432 #211 #543 #f60 #321',[[4,7,1,3,'#f60'],[10,10,2,1,'#f60'],[6,12,1,2,'#f60'],[1,6,2,5,'#654'],[13,6,2,5,'#654']]],
'Cinder Skeleton':['H','#333 #111 #444 #f60 #333',[[6,0,4,1,'#f80'],[14,3,1,10,'#f60']]],
'Fire Giant':['H','#f84 #b32 #a42 #ff0 #f60',[[4,5,8,4,'#f90'],[1,5,2,6,'#f84'],[13,5,2,6,'#f84']]],
'Phoenix':['W','#f63 #c21 #fd2 #fff #ff4',[[6,15,2,1,'#f90']]],
'Watcher':['O','#fff #408 #a4f #000 #fff',[]],
'Void Saucer':['U','#99c #446 #6f6 #8ff #99c',[[7,11,2,3,'#8ff']]],
'Alien Stalker':['H','#8da #486 #254 #000 #8da',[[4,3,3,2,'#000'],[9,3,3,2,'#000'],[1,6,2,1,'#8da']]],
'Night Bat':['W','#424 #212 #636 #f33 #424',[[3,1,1,2,'#424'],[12,1,1,2,'#424']]],
'Shade Spider':['S','#223 #112 #546 #f22 #223',[[7,5,2,1,'#f22'],[7,9,2,2,'#a2a']]],
'Shadow Wraith':['G','#213 #102 #546 #f0f #213',[]],
'Tentacle Horror':['K','#3a8 #164 #8fc #ff0 #3a8',[[3,4,2,2,'#fff'],[11,4,2,2,'#fff'],[7,2,2,2,'#f6a']]],
'Chaos Beast':['B','#a3c #52a #3ce #ff0 #f4a',[[3,3,2,2,'#fff'],[10,3,2,2,'#fff'],[6,9,3,2,'#f4a']]],
'Rift Spawn':['G','#f5d #92a #5ef #fff #f5d',[[4,8,2,2,'#5ef'],[10,6,2,2,'#5ef'],[7,10,2,2,'#fff']]],
'Harpy':['W','#eb9 #a65 #ddd #f33 #c63',[[3,4,2,1,'#c63']]],
'Spectral Steed':['B','#cef #8ac #fff #36f #8cf',[[7,1,2,6,'#8cf'],[4,5,1,3,'#fff']]],
'Marble Titan':['H','#eee #bbb #ddd #fc4 #fc4',[[3,6,10,1,'#fc4'],[14,2,1,12,'#fc4']]],
'Sun Lion':['B','#fc4 #d82 #fd7 #420 #f90',[[0,1,3,8,'#f90'],[13,1,3,8,'#f90'],[3,0,10,2,'#f90']]],
'Bronze Bull':['B','#b73 #742 #964 #f22 #fff',[[2,0,2,3,'#fff'],[12,0,2,3,'#fff'],[7,6,2,2,'#fbb']]],
'Oracle Eye':['O','#fff #fc4 #4cf #000 #fff',[[3,0,2,1,'#fc4'],[11,0,2,1,'#fc4'],[7,0,2,1,'#fc4']]],
'Fallen Angel':['H','#fdb #889 #223 #f33 #223',[[0,5,3,6,'#333'],[13,5,3,6,'#333'],[5,0,6,1,'#fc4']]],
'Divine Guardian':['H','#fe9 #c92 #fc4 #35f #fff',[[0,6,4,6,'#fff'],[1,8,2,2,'#fc4'],[14,1,1,13,'#fe9']]],
'Judgement':['H','#fff #99b #ddf #000 #fff',[[4,3,8,1,'#000'],[0,6,1,5,'#fc4'],[14,6,1,5,'#fc4'],[13,3,3,1,'#fc4']]]};
function entry(){const m=$('mon'),b=mon.boss;m.animate([{transform:'translateX(-50%) translateY(-90px)',opacity:0},{transform:'translateX(-50%) translateY(0)',opacity:1,offset:.7},{transform:'translateX(-50%) translateY(0)',opacity:1}],{duration:b?700:450,easing:'steps(6)'});setTimeout(()=>{const c=cc($('me'));boom([c[0],c[1]+60],'#e9d9a8',8,40);if(b)fx($('stage'),'shake',300)},b?450:300)}
function ambient(w){const s=$('stage');s.querySelectorAll('.amb').forEach(e=>e.remove());const c=[['#e9d9a8',1],['#fff',1],['#ff9a3a',-1],['#e07dff',0],['#ffe97a',-1]][w];for(let i=0;i<18;i++){const d=document.createElement('div'),sz=3+Math.floor(Math.random()*3)*2,T=c[1]<0?'100%':c[1]>0?'-5%':Math.random()*80+'%';d.className='amb';d.style.cssText=`position:absolute;z-index:1;left:${Math.random()*100}%;top:${T};width:${sz}px;height:${sz}px;background:${c[0]};pointer-events:none;opacity:.8`;s.appendChild(d);d.animate(c[1]==0?[{opacity:0},{opacity:1},{opacity:0}]:[{transform:'translate(0,0)'},{transform:`translate(${(Math.random()-.5)*60}px,${c[1]*310}px)`}],{duration:3000+Math.random()*3000,delay:-Math.random()*5000,iterations:Infinity,easing:'steps(40)'})}}
let AW=-1;function theme(w){const c=WD[w].c,s=document.documentElement.style;s.setProperty('--wl',c[0]);s.setProperty('--wm',c[1]);s.setProperty('--wf',c[2]);if(AW!=w){AW=w;ambient(w)}}
W.forEach(x=>{if(x[2]==8){x[2]=11;x[1]=Math.round(x[1]*1.5)}});A.forEach(x=>{if(x[2]==8){x[2]=11;x[1]=Math.round(x[1]*1.6)}});
RN.splice(8,1,'Primal','Ancient','Abyssal','Godly');
const CR=[0,.2,0,.3,.4,0,0,.25],LF=[0,0,.2,0,0,.2,.3,.1];
[[[['Toxic Fang','🐍'],['Bog Cleaver','🪓'],['Spore Mace','🍄'],['Venom Spear','🔱'],['Rotwood Bow','🏹'],['Plague Blade','🦠'],['Vine Scythe','🌿'],['Frog King Rod','🐸']],8,44],[[['Sandstorm Blade','🏜️'],['Scorpion Sting','🦂'],['Cactus Flail','🌵'],['Pyramid Spike','🔺'],['Horus Bow','🏹'],['Canopic Club','🏺'],['Anubis Scythe','🌙'],['Eye of Ra','👁️']],9,54],[[['Tidal Trident','🔱'],['Kraken Fang','🦑'],['Shark Tooth Axe','🦈'],['Conch Hammer','🐚'],['Pearl Bow','🏹'],['Anglerfish Lance','🐠'],['Octo Whip','🐙'],['Crab Claw Mace','🦀']],10,64]].forEach(([L,t,b])=>L.forEach((x,i)=>W.push([x[0],b+i*2,t,CR[i],LF[i],x[1]])));
const NR0=W.length;
[['Gator Jawblade','🐊',52,0,.2],['Hydra Fang','🐉',55,.2,0],['Plague Doctor Cane','🎩',60,0,.25],['Sandworm Tooth','🦷',62,.25,0],['Mummy Scepter','🧿',66,0,.3],['Sphinx Riddle Blade','🗿',70,.3,0],['Leviathan Spine','🌊',72,0,.3],['Siren Trident','🧜',76,.35,0],['Maw Fang','🕳️',82,.25,.2]].forEach((x,i)=>W.push([x[0],x[2],8+Math.floor(i/3),x[3],x[4],x[1]]));
[['Bog Hide',20,8,0,'🐊'],['Spore Robe',23,8,.25,'🍄'],['Mossy Plate',26,8,0,'🌿'],['Pharaoh Mail',26,9,0,'👑'],['Sand Cloak',29,9,.25,'🏜️'],['Scarab Plate',32,9,.1,'🛡️'],['Coral Armour',32,10,0,'🐚'],['Tide Robe',35,10,.3,'🌊'],['Leviathan Scale',38,10,.1,'🐋']].forEach(a=>A.push(a));
Object.assign(AC,{'Bog Hide':'#6a8a3a','Spore Robe':'#9a7ac8','Mossy Plate':'#5a7a4a','Pharaoh Mail':'#e8c85a','Sand Cloak':'#d8b878','Scarab Plate':'#2a8a6a','Coral Armour':'#ff8a9a','Tide Robe':'#3a9ad8','Leviathan Scale':'#2a5a8a'});
WI.push(...W.slice(WI.length).map(x=>x[5]));AI.push(...A.slice(AI.length).map(x=>x[4]));
const isR=i=>(i>=RW0&&i<RW0+15)||(i>=NR0&&i<NR0+9),RWL=f=>f<12?RW0+f:f<21?NR0+f-12:RW0+f-9;
function dropW(t){const ok=i=>!g.iw.includes(i)&&!isR(i);for(let d=0;d<12;d++)for(const tt of d?[t-d,t+d]:[t]){const c=W.map((x,i)=>i).filter(i=>W[i][2]==tt&&ok(i));if(c.length){giveW(c[r(0,c.length-1)],1);return}}log('You have collected every weapon!')}
const st=(L,j,boss)=>{const s=L<=11?1+(L-3)*.24:2.92+(L-11)*.12,a=(L-3)*2.2,wb=L%3==2;return boss?[Math.round((170+(wb?60:0))*s),Math.round(20+a+(wb?3:0))]:[Math.round((80+j*10)*s),Math.round(16+j+a)]};
F.splice(12,0,...[['Bog Entrance','Bog Toad','Mud Crawler','Spore Zombie','Gator King'],['Mushroom Grove','Fungal Sprout','Shroom Brute','Spore Sprite','Hydra'],['Plague Marsh','Plague Rat','Swamp Witch','Rot Golem','Plague Doctor'],['Dune Sea','Sand Scorpion','Dust Devil','Desert Bandit','Sandworm'],['Pyramid Halls','Mummy','Scarab Swarm','Tomb Guard','Mummy Lord'],['Sphinx Chamber','Cursed Cat','Sand Wraith','Sun Priest','The Sphinx'],['Coral Gate','Crab Soldier','Jelly Drifter','Piranha Pack','Leviathan'],['Shipwreck Depths','Drowned Sailor','Anglerfish','Sea Serpent','Siren Queen'],['Abyssal Trench','Deep Lurker','Giant Squid','Void Fish','Abyssal Maw']].map((x,i)=>{const L=12+i;return{n:x[0],m:[1,2,3].map(j=>['?',x[j],...st(L,j)]),b:['?',x[4],...st(L,0,1)]}}));
F.slice(21).forEach((l,i)=>{const L=21+i;l.m.forEach((m,j)=>{const q=st(L,j+1);m[2]=q[0];m[3]=q[1]});const q=st(L,0,1);l.b[2]=q[0];l.b[3]=q[1]});
WD.splice(4,0,{n:'Toxic Swamp',c:['#b8d890','#7a9a5a','#5a7a3a','#9be85a']},{n:'Sand Tombs',c:['#f0d8a0','#c9a860','#a8884a','#f3d27a']},{n:'Sunken Abyss',c:['#7ac8e0','#4a98b8','#2a6a8a','#6ae0ff']});
NA.splice(4,0,[['shoot','🧪',2,32,'arc'],['chomp'],['shoot','🦠',2,32,'wave']],[['claw'],['shoot','🪨',2,36,'rain'],['shoot','💨',1,40,'line']],[['shoot','💧',3,32,'rain'],['chomp'],['shoot','🌊',1,44,'line']]);
Object.assign(BB,{'Gator King':['charge'],'Hydra':['shoot','🧪',5,40,'fan'],'Plague Doctor':['shoot','🦠',4,36,'wave'],'Sandworm':['quake'],'Mummy Lord':['multi',[['shoot','🏺',2,44,'arc'],['nova','#ffe14a']]],'The Sphinx':['beam','#ffd84a'],'Leviathan':['multi',[['nova','#4af'],['shoot','🌊',3,56,'line']]],'Siren Queen':['shoot','🎵',5,36,'wave'],'Abyssal Maw':['multi',[['nova','#f35'],['blink'],['beam','#f35']]]});
Object.assign(BS,{'Gator King':{t:'D',p:['#4a3','#271','#db6','#ff3','#fe9'],x:[[3,0,10,1,'#fc4']]},'Hydra':{t:'K',p:['#3a6','#164','#af7','#ff3','#3a6'],x:[[2,0,2,4,'#3a6'],[12,0,2,4,'#3a6'],[2,0,1,1,'#ff3'],[13,0,1,1,'#ff3'],[7,0,2,3,'#3a6']]},'Plague Doctor':{t:'H',p:['#ddd','#444','#333','#6f6','#333'],x:[[6,4,4,3,'#fc6'],[14,2,1,12,'#642'],[13,0,3,3,'#6f6']]},'Sandworm':{t:'N',p:['#c93','#864','#fd8','#f22','#c93'],x:[[3,1,10,1,'#fd8'],[5,3,1,2,'#fff'],[10,3,1,2,'#fff']]},'Mummy Lord':{t:'H',p:['#ddc','#99a','#eec','#3ff','#fc4'],x:[[0,6,2,6,'#eec'],[14,6,2,6,'#eec'],[14,0,1,6,'#3ff']]},'The Sphinx':{t:'B',p:['#eb7','#a74','#fc4','#35f','#35f'],x:[[3,0,10,3,'#35f'],[4,3,1,3,'#fc4'],[11,3,1,3,'#fc4']]},'Leviathan':{t:'D',p:['#27a','#135','#8de','#ff3','#4af'],x:[[6,0,4,2,'#4af']]},'Siren Queen':{t:'H',p:['#fde','#38a','#3ad','#f3a','#5ef'],x:[[2,2,2,10,'#f6a'],[12,2,2,10,'#f6a'],[14,2,1,10,'#fc4'],[13,1,3,3,'#5ef']]},'Abyssal Maw':{t:'K',p:['#222','#000','#f35','#ff3','#222'],x:[[3,4,2,2,'#f35'],[11,4,2,2,'#f35'],[4,7,8,1,'#fff'],[6,5,4,2,'#f35']]}});
Object.assign(MS,{'Bog Toad':['R','#6a4 #373 #bd7 #ff3 #6a4',[[3,3,2,1,'#ff3'],[11,3,2,1,'#ff3']]],'Mud Crawler':['S','#753 #421 #a85 #ff3 #753',[]],'Spore Zombie':['H','#9b7 #564 #675 #f33 #7a5',[[4,1,2,1,'#e8d'],[10,0,2,2,'#e8d']]],'Fungal Sprout':['G','#c8a #825 #fdb #222 #e46',[[2,0,12,2,'#e46'],[5,0,1,1,'#fff'],[9,1,1,1,'#fff']]],'Shroom Brute':['B','#a85 #642 #ec9 #111 #d33',[[1,0,14,3,'#d33'],[4,1,1,1,'#fff'],[10,0,1,1,'#fff']]],'Spore Sprite':['W','#bf8 #7a4 #fff #333 #e6d',[]],'Plague Rat':['R','#7a6 #453 #cb7 #f33 #cb7',[[15,9,1,4,'#cb7']]],'Swamp Witch':['H','#8c8 #264 #408 #ff3 #306',[[3,0,10,2,'#306'],[14,2,1,12,'#842']]],'Rot Golem':['H','#583 #342 #453 #cf3 #342',[[2,6,2,2,'#7a4'],[10,9,3,2,'#7a4'],[1,6,2,5,'#564'],[13,6,2,5,'#564']]],
'Sand Scorpion':['S','#db6 #964 #fc8 #f22 #db6',[[12,2,3,3,'#fc8'],[14,0,2,3,'#fc8'],[0,7,3,2,'#db6'],[13,7,3,2,'#db6']]],'Dust Devil':['G','#ca7 #986 #edb #333 #ca7',[[3,1,1,1,'#edb'],[12,4,1,1,'#edb']]],'Desert Bandit':['H','#db9 #964 #a53 #222 #c33',[[4,5,8,2,'#c33'],[14,6,1,6,'#ccc']]],'Mummy':['H','#ddc #aa9 #eed #f22 #ddc',[[3,6,10,1,'#aa9'],[3,9,10,1,'#aa9'],[4,3,1,2,'#aa9']]],'Scarab Swarm':['S','#2a7 #164 #4ec #ff3 #2a7',[[3,3,2,2,'#4ec'],[11,3,2,2,'#4ec']]],'Tomb Guard':['H','#cb7 #864 #fc4 #35f #fc4',[[14,1,1,13,'#fc4'],[13,0,3,2,'#35f'],[4,0,8,1,'#35f']]],'Cursed Cat':['R','#222 #111 #648 #fe3 #222',[[3,2,1,2,'#222'],[12,2,1,2,'#222'],[15,8,1,5,'#222']]],'Sand Wraith':['G','#eb8 #b85 #ffd #333 #eb8',[]],'Sun Priest':['H','#fb7 #a62 #fe8 #c22 #fc4',[[3,0,10,2,'#fc4'],[14,1,1,13,'#a62'],[13,0,3,3,'#fe8']]],
'Crab Soldier':['S','#e55 #a22 #fa8 #ff3 #e55',[[0,6,3,3,'#e55'],[13,6,3,3,'#e55']]],'Jelly Drifter':['G','#f9c #c59 #fde #333 #f9c',[[2,13,1,3,'#f9c'],[5,14,1,2,'#f9c'],[10,14,1,2,'#f9c'],[13,13,1,3,'#f9c']]],'Piranha Pack':['R','#5a8 #264 #f55 #fff #5a8',[[4,8,8,1,'#fff']]],'Drowned Sailor':['H','#8bb #455 #334 #ff3 #234',[[3,0,10,1,'#234'],[14,2,1,10,'#876'],[2,12,3,2,'#6a8']]],'Anglerfish':['B','#357 #123 #6af #fff #ff6',[[7,0,2,2,'#ff6'],[4,7,8,1,'#fff']]],'Sea Serpent':['N','#3a9 #167 #8fd #ff3 #3a9',[]],'Deep Lurker':['K','#336 #113 #66c #f3f #336',[[7,3,2,3,'#f3f']]],'Giant Squid':['K','#d57 #824 #fac #ff3 #d57',[[3,4,2,2,'#fff'],[11,4,2,2,'#fff'],[5,0,6,2,'#d57']]],'Void Fish':['W','#a5f #52a #fff #ff3 #a5f',[]]});
function ambient(w){const s=$('stage');s.querySelectorAll('.amb').forEach(e=>e.remove());const c=[['#e9d9a8',1],['#fff',1],['#ff9a3a',-1],['#e07dff',0],['#9be85a',-1],['#f3d27a',1],['#6ae0ff',-1],['#ffe97a',-1]][w];for(let i=0;i<18;i++){const d=document.createElement('div'),sz=3+Math.floor(Math.random()*3)*2,T=c[1]<0?'100%':c[1]>0?'-5%':Math.random()*80+'%';d.className='amb';d.style.cssText=`position:absolute;z-index:1;left:${Math.random()*100}%;top:${T};width:${sz}px;height:${sz}px;background:${c[0]};pointer-events:none;opacity:.8`;s.appendChild(d);d.animate(c[1]==0?[{opacity:0},{opacity:1},{opacity:0}]:[{transform:'translate(0,0)'},{transform:`translate(${(Math.random()-.5)*60}px,${c[1]*310}px)`}],{duration:3000+Math.random()*3000,delay:-Math.random()*5000,iterations:Infinity,easing:'steps(40)'})}}
const TC=['#d6dbe0','#7bff8a','#63b8ff','#e0a8ff','#ffc83a','#5ff3ff','#ff8a3a','#e07dff','#9be85a','#ffcf6a','#4ad8ff','#fff6a0'],HC=['#6b4423','#4a3020','#8a5a2b','#3a3a48','#7a2a2a'],WEC={};
const mx=(a,b,p)=>{const f=h=>[1,3,5].map(i=>parseInt(h.substr(i,2),16));const A=f(a),B=f(b);return '#'+A.map((v,i)=>Math.round(v*(1-p)+B[i]*p).toString(16).padStart(2,'0')).join('')};
const WT=[[/Thunderbolt/,'bolt'],[/Bow/i,'bow'],[/Scythe|Reaper/,'scythe'],[/Axe|Cleaver|Pickaxe/,'axe'],[/Hammer|Maul|Anvil|Anchor|Tools|Magnet/,'hammer'],[/Mace|Flail|Fist/,'mace'],[/Pan$/,'pan'],[/Club|Stick|Bone/,'club'],[/Spear|Lance|Trident|Spike|Poseidon/,'spear'],[/Dagger|Fang|Tooth|Sting|Talon|Dart|Tusk|Jawbone/,'dagger'],[/Staff|Scepter|Rod|Cane|Broom|Eye of/,'staff'],[/Orb|Bomb|Spiral/,'orb'],[/Whip|Chain/,'whip']];
function wsvg(id){const w=W[id],n=w[0],t=w[2],ty=(WT.find(q=>q[0].test(n))||[0,'sword'])[1],h=[...n].reduce((a,c)=>(a*31+c.charCodeAt(0))>>>0,7),v=h>>3,tc=TC[t]||TC[0];let bl=mx(tc,'#dfe6ee',t<5?.55:.25);if(w[4])bl=mx(bl,'#d0204a',.3);
 const dk=mx(bl,'#000000',.45),hc=HC[h%5],gem=`hsl(${h%360},85%,60%)`,gd=mx(tc,'#8a6a20',.55),R=(x,y,a,b,f,r)=>`<rect x='${x}' y='${y}' width='${a}' height='${b}' rx='${r||2}' fill='${f}'/>`;
 const bld=(y0,y1,bw,cv,fl)=>cv?`<path d='M32 ${y0}Q${40+bw} ${y0+18} ${35+bw} ${y1}H${29-bw}Q${30-bw} ${y0+18} 32 ${y0}Z' fill='url(#b)'/>`:fl?`<path d='M32 ${y0}L${32+bw} ${y0+7}L${29+bw} ${y0+13}L${33+bw} ${y0+19}L${29+bw} ${y0+25}L${33+bw} ${y0+31}L${32+bw} ${y1}H${32-bw}L${31-bw} ${y0+31}L${35-bw} ${y0+25}L${31-bw} ${y0+19}L${35-bw} ${y0+13}L${31-bw} ${y0+7}Z' fill='url(#b)'/>`:`<path d='M32 ${y0}L${32+bw} ${y0+7}V${y1}H${32-bw}V${y0+7}Z' fill='url(#b)'/>`;
 let b='';
 if(ty=='sword'||ty=='dagger'){const dg=ty=='dagger',bw=dg?2.5+v%2:3+v%3,y0=dg?12:2,y1=dg?38:42,gs=(v>>2)%3,cv=(v>>4)%4==1||/Fang|Tooth|Tusk|Talon|Jawbone/.test(n),fl=(v>>6)%4==0&&!dg&&t>=3;
  b=bld(y0,y1,bw,cv,fl)+`<path d='M32 ${y0+6}V${y1-2}' stroke='${dk}' stroke-width='1.1' fill='none'/>`+(gs==0?R(dg?24:20,y1,dg?16:24,4.5,gd):gs==1?`<path d='M${dg?22:18} ${y1-2}Q32 ${y1+9} ${dg?42:46} ${y1-2}L${dg?40:44} ${y1+4}H${dg?24:20}Z' fill='${gd}'/>`:`<ellipse cx='32' cy='${y1+2}' rx='${dg?9:13}' ry='3.5' fill='${gd}'/>`)+R(29.5,y1+4,5,dg?14:12,'url(#h)')+`<circle cx='32' cy='${y1+(dg?20:18)}' r='3.5' fill='${gem}'/><circle cx='32' cy='${y1+2.2}' r='2.2' fill='${gem}'/>`}
 else if(ty=='staff'){const k=v%3;b=R(30,16,4,46,'url(#h)')+(k==0?`<path d='M23 16Q22 2 32 2Q42 2 41 16' fill='none' stroke='${gd}' stroke-width='3'/><circle cx='32' cy='11' r='6.5' fill='${gem}'/><circle cx='30' cy='9' r='1.8' fill='#fff' stroke='none'/>`:k==1?`<path d='M32 0L41 11L32 24L23 11Z' fill='${gem}'/><path d='M32 3L36 11L32 20' fill='none' stroke='#fff' stroke-opacity='.6'/>`:`<path d='M24 14L28 2L32 10L36 2L40 14Z' fill='${gd}'/><circle cx='32' cy='12' r='5' fill='${gem}'/>`)+R(27,40,10,4,gd)}
 else if(ty=='axe'){b=R(30,8,4,52,'url(#h)')+`<path d='M34 10Q58 6 56 30Q46 24 34 28Z' fill='url(#b)'/>`+(v%2?`<path d='M30 10Q6 6 8 30Q18 24 30 28Z' fill='url(#b)'/>`:'')+`<circle cx='32' cy='19' r='2.4' fill='${gem}'/>`}
 else if(ty=='hammer'){b=R(30,22,4,40,'url(#h)')+R(13,4,38,20,'url(#b)',3)+`<path d='M23 4V24M41 4V24' stroke='${dk}' fill='none'/><circle cx='32' cy='14' r='3.2' fill='${gem}'/>`+(v%2?`<path d='M19 4L22 0L25 4M39 4L42 0L45 4' fill='${bl}'/>`:'')}
 else if(ty=='mace'){const sp=[...Array(8)].map((_,k)=>{const a=k*Math.PI/4,c=Math.cos,s=Math.sin;return `<path d='M${32+c(a-.25)*10} ${15+s(a-.25)*10}L${32+c(a)*17} ${15+s(a)*17}L${32+c(a+.25)*10} ${15+s(a+.25)*10}Z' fill='${dk}'/>`}).join('');b=R(30,24,4,38,'url(#h)')+sp+`<circle cx='32' cy='15' r='11' fill='url(#b)'/><circle cx='32' cy='15' r='3.4' fill='${gem}'/>`}
 else if(ty=='club'){const bn=/Bone/.test(n),cf=bn?'#ece3cc':'url(#h)';b=`<path d='M27 4Q32 0 37 4L40 18L35 60H29L24 18Z' fill='${cf}'/><circle cx='30' cy='24' r='1.6' fill='${dk}'/><circle cx='34' cy='36' r='1.4' fill='${dk}'/>`+(bn?`<circle cx='26' cy='8' r='4' fill='${cf}'/><circle cx='38' cy='8' r='4' fill='${cf}'/>`:`<path d='M26 42H38' stroke='${gd}' stroke-width='3'/>`)}
 else if(ty=='pan'){b=R(30,30,4,32,'url(#h)')+`<circle cx='32' cy='17' r='15' fill='url(#b)'/><circle cx='32' cy='17' r='10' fill='none' stroke='${dk}'/><circle cx='28' cy='13' r='3' fill='#fff' fill-opacity='.4' stroke='none'/>`}
 else if(ty=='spear'){b=R(30.5,18,3,44,'url(#h)')+(/Trident|Poseidon/.test(n)?`<path d='M32 6V50M18 8V18Q18 28 32 28Q46 28 46 18V8' fill='none' stroke='url(#b)' stroke-width='3.5'/><path d='M18 2L21 9H15ZM32 0L35 7H29ZM46 2L49 9H43Z' fill='${bl}'/>`:`<path d='M32 0L39 16L32 22L25 16Z' fill='url(#b)'/><path d='M32 22Q26 28 28 34M32 22Q38 28 36 34' stroke='${gd}' stroke-width='2' fill='none'/><circle cx='32' cy='14' r='2.2' fill='${gem}'/>`)}
 else if(ty=='scythe'){b=R(30,6,4,56,'url(#h)')+`<path d='M32 8Q62 4 58 34Q54 18 32 16Z' fill='url(#b)'/><circle cx='32' cy='12' r='3' fill='${gem}'/>`}
 else if(ty=='bow'){b=`<path d='M46 3Q10 32 46 61' fill='none' stroke='${hc}' stroke-width='4.5'/><path d='M46 3Q10 32 46 61' fill='none' stroke='${tc}' stroke-width='1.5'/><path d='M46 3V61' stroke='#e8e0d0' stroke-width='1' fill='none'/><path d='M14 32H56' stroke='${hc}' stroke-width='2' fill='none'/><path d='M56 32L48 28V36Z' fill='${bl}'/><path d='M14 32L10 28M14 32L10 36' stroke='${tc}' fill='none'/><circle cx='22' cy='32' r='2.4' fill='${gem}'/>`}
 else if(ty=='bolt'){b=`<path d='M40 2L16 36H30L22 62L50 24H35Z' fill='${tc}'/><path d='M38 8L24 32' stroke='#fff' stroke-opacity='.7' fill='none'/>`}
 else if(ty=='orb'){b=R(28,44,8,16,'url(#h)')+`<path d='M18 40Q32 50 46 40L44 46H20Z' fill='${gd}'/><circle cx='32' cy='26' r='18' fill='${gem}'/><circle cx='26' cy='20' r='6' fill='#fff' fill-opacity='.5' stroke='none'/><path d='M18 28Q32 12 46 28Q32 40 18 28Z' fill='none' stroke='${tc}' stroke-width='2'/>`}
 else if(ty=='whip'){b=R(28,48,8,14,'url(#h)')+`<path d='M32 50Q8 44 20 30Q44 24 34 12Q30 6 46 4' fill='none' stroke='${hc}' stroke-width='3.5'/><path d='M34 12Q30 6 46 4' fill='none' stroke='${tc}' stroke-width='2'/><circle cx='46' cy='4' r='2.5' fill='${gem}'/>`}
 else{b=bld(2,42,4,0,0)+R(20,42,24,4.5,gd)+R(29.5,46,5,12,'url(#h)')}
 return `<svg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 64 64'><defs><linearGradient id='b' x1='0' x2='1'><stop offset='0' stop-color='${mx(bl,'#ffffff',.6)}'/><stop offset='.5' stop-color='${bl}'/><stop offset='1' stop-color='${dk}'/></linearGradient><linearGradient id='h' x1='0' x2='1'><stop offset='0' stop-color='${mx(hc,'#ffffff',.25)}'/><stop offset='1' stop-color='${mx(hc,'#000000',.4)}'/></linearGradient><radialGradient id='g'><stop offset='0' stop-color='${tc}' stop-opacity='.55'/><stop offset='1' stop-color='${tc}' stop-opacity='0'/></radialGradient></defs>${t>=3?`<circle cx='32' cy='32' r='31' fill='url(#g)'/>`:''}<g stroke='#1a1020' stroke-width='1.5' stroke-linejoin='round' stroke-linecap='round'>${b}</g>${w[3]?`<path d='M53 6l2 5 5 2-5 2-2 5-2-5-5-2 5-2z' fill='#ffe14a' stroke='#a06a00' stroke-width='.6'/>`:''}${w[4]?`<path d='M10 6Q15 13 10 18Q5 13 10 6Z' fill='#d0204a' stroke='#600' stroke-width='.6'/>`:''}</svg>`}
function WE(id,s){return `<img class='wi' src='${WEC[id]||(WEC[id]='data:image/svg+xml;utf8,'+encodeURIComponent(wsvg(id)).replace(/'/g,'%27'))}' width='${s}' height='${s}' alt=''>`}
const AT=[[/Robe|Cloak/,'robe'],[/Scale/,'scale'],[/Mail/,'mail'],[/Plate|Armour|Aegis/,'plate']],AEC={};
function asvg(id){const a=A[id],n=a[0],t=a[2],ty=(AT.find(q=>q[0].test(n))||[0,'hide'])[1],h=[...n].reduce((c,d)=>(c*31+d.charCodeAt(0))>>>0,7),tc=TC[t]||TC[0],m=AC[n]||tc,lt=mx(m,'#ffffff',.4),dk=mx(m,'#000000',.45),tr=mx(tc,'#ffffff',.2),gem=`hsl(${h%360},85%,60%)`,TU='M18 14L26 10Q32 17 38 10L46 14L53 25L44 29V56H20V29L11 25Z';
 let b='',pt='';
 if(ty=='plate'){b=`<path d='${TU}' fill='url(#m)'/><circle cx='13' cy='21' r='9' fill='${lt}'/><circle cx='51' cy='21' r='9' fill='${lt}'/><path d='M22 14H42L45 32Q32 42 19 32Z' fill='${m}'/><path d='M32 14V40' stroke='${dk}' stroke-width='1.2' fill='none'/><rect x='20' y='44' width='24' height='5' fill='${tr}'/><path d='M22 49H42L40 58H24Z' fill='${m}'/><circle cx='32' cy='27' r='3.6' fill='${gem}'/>`}
 else if(ty=='robe'){b=`<path d='M22 10Q32 18 42 10L51 22L46 31L49 59H15L18 31L13 22Z' fill='url(#m)'/><path d='M22 10Q32 0 42 10Q32 17 22 10Z' fill='${dk}'/><rect x='18' y='36' width='28' height='5' fill='${tr}'/><path d='M32 17V58' stroke='${dk}' fill='none'/><path d='M15 59H49' stroke='${tr}' stroke-width='3'/><circle cx='32' cy='38.5' r='3' fill='${gem}'/>`}
 else if(ty=='mail'||ty=='scale'){pt=ty=='mail'?`<pattern id='p' width='6' height='6' patternUnits='userSpaceOnUse'><circle cx='3' cy='3' r='2.2' fill='none' stroke='${dk}' stroke-width='.9'/></pattern>`:`<pattern id='p' width='8' height='6' patternUnits='userSpaceOnUse'><path d='M0 6Q4 0 8 6' fill='none' stroke='${dk}' stroke-width='1'/></pattern>`;b=`<path d='${TU}' fill='url(#m)'/><path d='${TU}' fill='url(#p)' stroke='none'/><path d='M26 10Q32 17 38 10' fill='none' stroke='${tr}' stroke-width='2.4'/><rect x='20' y='46' width='24' height='4' fill='${tr}'/><circle cx='32' cy='48' r='2.4' fill='${gem}'/>`}
 else{const rg=/Rags|Torn/.test(n);b=`<path d='${TU}' fill='url(#m)'/>`+(rg?`<path d='M20 52V58L24 54L28 61L32 54L36 61L40 54L44 58V52Z' fill='${m}'/><path d='M26 30L31 34M38 40L34 45' stroke='${dk}' stroke-width='2' fill='none'/>`:`<path d='M32 14V38M26 19L38 24M26 26L38 31M26 33L38 38' stroke='${dk}' stroke-width='1.2' fill='none'/><rect x='20' y='44' width='24' height='5' fill='${dk}'/><circle cx='32' cy='46.5' r='2.4' fill='${gem}'/>`)+[23,29,35,41].map(x=>`<circle cx='${x}' cy='13' r='4' fill='#f5f0e6'/>`).join('')}
 return `<svg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 64 64'><defs><linearGradient id='m' x1='0' y1='0' x2='0' y2='1'><stop offset='0' stop-color='${lt}'/><stop offset='1' stop-color='${m}'/></linearGradient>${pt}<radialGradient id='g'><stop offset='0' stop-color='${tc}' stop-opacity='.55'/><stop offset='1' stop-color='${tc}' stop-opacity='0'/></radialGradient></defs>${t>=3?`<circle cx='32' cy='32' r='31' fill='url(#g)'/>`:''}<g stroke='#1a1020' stroke-width='1.5' stroke-linejoin='round' stroke-linecap='round'>${b}</g>${a[3]?`<path d='M4 44Q14 40 10 32M60 44Q50 40 54 32' stroke='#8ff' stroke-width='2' fill='none' stroke-linecap='round'/>`:''}</svg>`}
const SHM=(t,s,src)=>`<img class='wi${t>=4?' sh':''}' src='${src}' style='--sc:${TC[t]};animation-duration:${Math.max(1,3.2-t*.2)}s' width='${s}' height='${s}' alt=''>`;
function WE(id,s){return SHM(W[id][2],s,WEC[id]||(WEC[id]='data:image/svg+xml;utf8,'+encodeURIComponent(wsvg(id)).replace(/'/g,'%27')))}
function AE(id,s){return SHM(A[id][2],s,AEC[id]||(AEC[id]='data:image/svg+xml;utf8,'+encodeURIComponent(asvg(id)).replace(/'/g,'%27')))}
let fz={k:0,sel:[],res:null,msg:'',busy:0};
function openFz(k){if(!$('home').classList.contains('hide')){const s=load();if(!s)return;g=s;if(!g.iw){g.iw=[0];g.ia=[0];g.w=0;g.a=0}g.nw=g.nw||0}fz={k:k||0,sel:[],res:null,msg:'',busy:0};drawFz();$('fz').classList.remove('hide')}
function closeFz(){if(fz.busy)return;$('fz').classList.add('hide');if($('home').classList.contains('hide'))ui();else home()}
function fzK(k){if(fz.busy)return;fz={k,sel:[],res:null,msg:'',busy:0};drawFz()}
function fzRow(id){const L=fz.k?A:W,x=L[id],t=x[2],eq=id==(fz.k?g.a:g.w),f=fz.sel.length?L[fz.sel[0]][2]:t,s=fz.sel.includes(id),off=eq||t>=11;return `<div class='it${s?' sel':''}${(off||t!=f)&&!s?' dim':''}' style='--c:var(--t${t})' data-i='${id}' data-d='${off?1:0}'>${fz.k?AE(id,40):WE(id,40)}<div><b>${x[0]}</b><small>${RN[t]} - ${fz.k?'-'+x[1]+' dmg':'+'+x[1]+' atk'} ${pk(x,fz.k)}</small></div><span>${eq?'EQUIPPED':t>=11?'MAX':s?'SELECTED':''}</span></div>`}
function drawFz(){const L=fz.k?A:W,own=fz.k?g.ia:g.iw,sel=fz.sel,t=sel.length?L[sel[0]][2]:null,ids=[...own].sort((a,b)=>L[b][1]-L[a][1]);
 const slot=i=>sel[i]!=null?`<div class='fzs f' style='--c:var(--t${L[sel[i]][2]});--mx:${(1-i)*72}px'>${fz.k?AE(sel[i],44):WE(sel[i],44)}</div>`:`<div class='fzs' style='--mx:${(1-i)*72}px'>?</div>`;
 const info=fz.msg||(t==null?'PICK 3 ITEMS OF THE SAME RARITY. THEY FUSE INTO 1 ITEM OF THE NEXT RARITY (10% CHANCE TO JUMP 2).':sel.length<3?'SELECT '+(3-sel.length)+' MORE '+RN[t].toUpperCase()+' ITEMS':RN[t].toUpperCase()+' x3 > '+RN[Math.min(11,t+1)].toUpperCase());
 $('fzc').innerHTML=`<div class='fzh'><span>FUSION</span><button onclick='closeFz()' style='padding:6px 10px;font-size:8px'>CLOSE</button></div><div class='fzt'><button class='${fz.k?'':'on'}' onclick='fzK(0)'>WEAPONS</button><button class='${fz.k?'on':''}' onclick='fzK(1)'>ARMOUR</button></div><div id='fzch' class='fzc'>${slot(0)}${slot(1)}${slot(2)}<span class='ar'>&gt;</span><div class='fzs${fz.res?' f':''}' id='fzo' style='--c:${fz.col||'var(--bd)'}'>${fz.res||'?'}</div></div><p style='font-size:8px;color:var(--gold);line-height:1.8;margin:0 0 8px'>${info}</p><button id='fzb' ${sel.length<3?'disabled':''} onclick='doFuse()' style='width:100%;padding:10px;font-size:10px'>FUSE</button><div style='margin-top:10px'>${ids.map(fzRow).join('')}</div>`;
 document.querySelectorAll('#fzc .it').forEach(e=>e.onclick=()=>{if(e.dataset.d=='1'||fz.busy)return;const i=+e.dataset.i;if(fz.sel.includes(i))fz.sel=fz.sel.filter(x=>x!=i);else if(fz.sel.length<3&&(!fz.sel.length||L[fz.sel[0]][2]==L[i][2]))fz.sel.push(i);fz.res=null;fz.msg='';drawFz()})}
async function doFuse(){if(fz.sel.length<3||fz.busy)return;const L=fz.k?A:W,own=fz.k?g.ia:g.iw,sel=fz.sel,t=L[sel[0]][2],nt=Math.min(11,t+1+(Math.random()<.1?1:0));let pick=null;
 for(let d=0;d<12&&pick==null;d++)for(const u of d?[nt-d,nt+d]:[nt]){if(u<=t||u>11)continue;const c=L.map((x,i)=>i).filter(i=>L[i][2]==u&&!own.includes(i)&&!(!fz.k&&isR(i)));if(c.length){pick=c[r(0,c.length-1)];break}}
 if(pick==null){fz.msg='NOTHING NEW LEFT TO FUSE INTO!';drawFz();return}
 fz.busy=1;$('fzch').classList.add('go');$('fzb').disabled=true;await wait(950);
 sel.forEach(i=>own.splice(own.indexOf(i),1));own.push(pick);g.nw=(g.nw||0)+1;save();
 const it=L[pick],u=it[2];fz.res=fz.k?AE(pick,44):WE(pick,44);fz.col=`var(--t${u})`;fz.msg=`${u>t+1?'LUCKY FUSION! ':''}FUSED INTO ${it[0].toUpperCase()} (${RN[u].toUpperCase()})`;fz.sel=[];fz.busy=0;drawFz()}
TC.push('#ffffff');RN.push('Omega');
const GW0=W.length;W.push(['Godslayer',135,12,.5,.3,'🗡️'],['Genesis Staff',120,12,.35,.4,'🪐'],['Hydra Fang',100,12,.3,.2,'🐉']);
const GA0=A.length;A.push(['Aegis of Creation',70,12,.25,'🛡️'],['Halo Robe',60,12,.4,'👼'],['Hydra Scale',55,12,.2,'🐉']);
Object.assign(AC,{'Aegis of Creation':'#fff6c0','Halo Robe':'#fffbe0','Hydra Scale':'#3aa86a'});
WI.push(...W.slice(WI.length).map(x=>x[5]));AI.push(...A.slice(AI.length).map(x=>x[4]));
function tierN(f){const w=Math.floor(f/3),fi=f%3;if(!w)return Math.min(4,fi+r(0,1)+(fi==2&&Math.random()<.2?1:0));const T=Math.min(11,4+w);return Math.random()<.35+fi*.2?T:T-1}
function tierB(f){const w=Math.floor(f/3);return w?Math.min(11,4+w):f+1}
function dropW(t){const ok=i=>!g.iw.includes(i)&&!isR(i)&&W[i][2]<12;for(let d=0;d<13;d++)for(const tt of d?[t-d,t+d]:[t]){const c=W.map((x,i)=>i).filter(i=>W[i][2]==tt&&ok(i));if(c.length){giveW(c[r(0,c.length-1)],1);return}}log('You have collected every weapon!')}
F.push({n:'The Beyond',m:[['?','Seraph',...st(24,1)],['?','Wrath Angel',...st(24,2)],['?','Star Eater',...st(24,3)]],b:['?','God',2600,85]});
WD.push({n:'The Beyond',c:['#5a4a9a','#7a6ac0','#2a1f55','#ffffff']});
NA.push([['bolt'],['shoot','✨',3,32,'rain'],['nova','#ffffff']]);
Object.assign(MS,{'Seraph':['H','#fff6d8 #e0b84a #ffffff #5ab0ff #ffd84a',[[0,4,3,7,'#fff'],[13,4,3,7,'#fff'],[4,0,8,1,'#fff6a0']]],'Wrath Angel':['H','#ffd0b0 #a02a1a #c23a2a #ffe94a #7a1a10',[[0,4,3,7,'#e86a4a'],[13,4,3,7,'#e86a4a'],[14,2,1,12,'#ff8a2a']]],'Star Eater':['K','#1a1040 #0a0620 #7a5af0 #fff #1a1040',[[3,4,2,2,'#fff'],[11,4,2,2,'#fff'],[7,1,2,2,'#ffe97a'],[4,7,8,1,'#ffe97a']]]});
BS.God={t:'H',s:180,p:['#fff6d8','#e0b84a','#ffffff','#5ab0ff','#ffd84a'],x:[[0,3,3,9,'#fff'],[13,3,3,9,'#fff'],[0,1,2,3,'#ffe27a'],[14,1,2,3,'#ffe27a'],[4,0,8,1,'#fff6a0'],[14,0,1,15,'#ffd84a'],[13,0,3,2,'#5ab0ff'],[5,5,6,3,'#fff'],[7,9,2,3,'#ffd84a']]};
const _am=ambient;ambient=function(w){_am(w>7?3:w)};
const GP=[[['nova','#ffffff'],['bolt']],[['shoot','✨',7,40,'rain'],['beam','#ffe14a']],[['nova','#fff6a0'],['shoot','☀️',5,56,'fan'],['bolt'],['beam','#ffffff']]];
async function monAtk(){if(mon.n=='God'){const f=mon.hp/mon.max,ph=f>.66?0:f>.33?1:2;if(mon.ph!==ph){mon.ph=ph;if(ph){fx($('flash'),'on');fx($('stage'),'shake',300);toast(ph==1?'GOD RAGES!':'GOD ASCENDS!',11);log(ph==1?'God\'s light turns blinding!':'God unleashes his final form!')}}await doAtk(['multi',GP[ph]]);return}await doAtk(mon.boss?(BB[mon.n]||['quake']):NA[Math.floor(g.f/3)][(g.k+g.f)%3])}
function entry(){const m=$('mon'),b=mon.boss,god=mon.n=='God';m.classList.toggle('god',god);$('stage').classList.toggle('divine',god);m.animate([{transform:'translateX(-50%) translateY(-90px)',opacity:0},{transform:'translateX(-50%) translateY(0)',opacity:1,offset:.7},{transform:'translateX(-50%) translateY(0)',opacity:1}],{duration:b?700:450,easing:'steps(6)'});setTimeout(()=>{const c=cc($('me'));boom([c[0],c[1]+60],'#e9d9a8',8,40);if(b)fx($('stage'),'shake',300);if(god){fx($('flash'),'on');ring(c,'#fff6a0',8)}},b?450:300)}
async function finale(){busy=true;const cs=$('cs');cs.innerHTML="<canvas id='csc'></canvas><div id='cst'></div><div id='csi'></div>";cs.classList.remove('hide');
 const cv=$('csc'),q=cv.getContext('2d'),w0=cv.width=cs.clientWidth,h0=cv.height=cs.clientHeight,tx=$('cst'),say=(t,ms)=>{tx.textContent=t;return wait(ms)},S=Math.max(6,Math.min(14,Math.floor(Math.min(w0,h0*.8)/20))),G=BS.God,im=new Image();
 im.src=SP(G.t,G.p,G.x,180).match(/src="([^"]+)"/)[1];await im.decode();
 const oc=document.createElement('canvas');oc.width=oc.height=18;const oq=oc.getContext('2d');oq.drawImage(im,0,0);const px=oq.getImageData(0,0,18,18).data,P=[],stars=[...Array(90)].map(()=>({x:Math.random()*w0,y:Math.random()*h0,s:1+Math.floor(Math.random()*3),v:.2+Math.random()*.8}));
 for(let y=0;y<18;y++)for(let x=0;x<18;x++){const i=(y*18+x)*4;if(px[i+3]>0)P.push({x:w0/2+(x-9)*S,y:h0*.38+(y-9)*S,c:`rgb(${px[i]},${px[i+1]},${px[i+2]})`,vx:(Math.random()-.5)*9,vy:(Math.random()-1)*9,a:1})}
 let ph=0,stop=false;const t0=performance.now();
 (function loop(){if(stop)return;const t=performance.now()-t0;q.fillStyle=ph?'#05030c':'#2a1f55';q.fillRect(0,0,w0,h0);
  if(!ph){q.save();q.translate(w0/2,h0*.38);q.rotate(t/2500);q.fillStyle='rgba(255,244,170,.22)';for(let k=0;k<12;k++){q.rotate(Math.PI/6);q.fillRect(0,-12,Math.max(w0,h0),24)}q.restore()}
  else stars.forEach(s=>{s.y=(s.y+s.v)%h0;q.fillStyle=`rgba(255,255,255,${.4+.6*Math.abs(Math.sin(t/400+s.x))})`;q.fillRect(s.x,s.y,s.s*2,s.s*2)});
  P.forEach(p=>{if(!ph){q.fillStyle=p.c;q.fillRect(p.x+(Math.random()-.5)*4,p.y+(Math.random()-.5)*4,S,S)}else if(p.a>0){p.x+=p.vx;p.y+=p.vy;p.vy+=.18;p.a-=.007;q.globalAlpha=Math.max(0,p.a);q.fillStyle=p.c;q.fillRect(p.x,p.y,S,S);q.globalAlpha=1}});
  requestAnimationFrame(loop)})();
 await say('THE ETERNAL LIGHT BEGINS TO CRACK...',2200);
 cv.animate([{filter:'brightness(5)'},{filter:'none'}],{duration:900});ph=1;
 await say('GOD HAS FALLEN.',2400);
 await say('THE HEAVENS OPEN AND OFFER THEIR GREATEST TREASURES...',2200);
 tx.textContent='';const box=$('csi');
 for(const [k,id] of [[0,GW0],[0,GW0+1],[1,GA0],[1,GA0+1]]){const own=k?g.ia:g.iw;if(!own.includes(id))own.push(id);const x=(k?A:W)[id];box.insertAdjacentHTML('beforeend',`<div class='cc' style='box-shadow:0 0 16px #fff8'>${k?AE(id,96):WE(id,96)}<b>${x[0].toUpperCase()}</b><small>OMEGA - ${k?'-'+x[1]+' DMG':'+'+x[1]+' ATK'}</small></div>`);await wait(1100)}
 g.nw=(g.nw||0)+4;await say('YOU HAVE ASCENDED... BUT HELL STIRS BELOW.',2000);
 box.insertAdjacentHTML('beforeend',"<button id='csb' style='width:100%;padding:12px;margin-top:6px;font-size:11px'>DESCEND TO HELL</button>");
 await new Promise(res=>$('csb').onclick=res);
 stop=true;cs.classList.add('hide');cs.innerHTML='';await portal();g.f=27;g.k=0;g.hp=g.max;spawn()}
const HN=[['FIRE','#e8452a #8a1f10 #ffb347 #fff3a0 #3a1a10'],['FROST','#7fd0f5 #3a7ab0 #e6f7ff #fff #cfe8ff'],['VENOM','#7ac43a #3a6a1a #d8f07a #ff3bf0 #2a4a10'],['STORM','#8a8cff #3a3a9a #ffe94a #fff #ffe94a'],['SHADOW','#4a3a6a #1a1030 #8a5ad0 #ff3b3b #120a20'],['STONE','#a89a82 #6a5e4a #d6c8a8 #ff8a1a #5a4e3a'],['TIDE','#2a8ad0 #145a8a #7fe0e0 #fff #9fe8ff'],['VOID','#8a2ad0 #3a0a6a #e07dff #fff #e07dff'],['DIVINE','#ffe27a #c9962a #ffffff #5ab0ff #fff6a0']],HPS=[[10,8],[30,8],[50,8],[70,8],[90,8],[20,96],[40,96],[60,96],[80,96]];
Object.assign(TP,{J:['.5....5.','.55..55.','..111111','.1111111','.1114111','.1111111','.1111111','..113333','..122222','...12121','....1111','....1331','....1331','....1111','....1331','....1111']});
let HY={on:0,dm:Array(9).fill(0),seen:{},room:null,rm:null,code:'',HH:1,tg:0,over:0,nm:'HERO'};
const hyTot=i=>HY.dm[i]+Object.values(HY.seen).reduce((s,a)=>s+a[i],0),hyDead=i=>hyTot(i)>=HY.HH,hyAlive=()=>[0,1,2,3,4,5,6,7,8].filter(i=>!hyDead(i));
async function hyOpen(){HY.rm=null;try{HY.rm=window.claude&&claude.use?await claude.use('room'):null}catch(e){}
 $('hy').classList.remove('hide');
 $('hyc').innerHTML=`<div class='fzh'><span>BOSS MODE</span><button onclick='hyClose()' style='padding:6px 10px;font-size:8px'>BACK</button></div><div style='display:flex;justify-content:center;margin:14px 0'>${HN.map(h=>SP('J',h[1].split(' '),[],36)).join('')}</div><p>THE NINE-HEADED HYDRA. EACH HEAD HAS ITS OWN ELEMENT AND ATTACK. SLAY ALL 9 TO WIN THE HYDRA FANG AND HYDRA SCALE (OMEGA GEAR). FIGHT ALONE OR WITH FRIENDS.</p><button class='w' onclick='hyStart(0)'>SOLO FIGHT</button><button class='w' onclick='hyStart(1)' ${HY.rm?'':'disabled'}>CREATE PARTY</button><input id='hycode' maxlength='8' placeholder='PARTY CODE'><button class='w' onclick='hyStart(2)' ${HY.rm?'':'disabled'}>JOIN PARTY</button><p id='hyerr' style='color:var(--gold)'>${HY.rm?'FRIENDS NEED THIS PAGE LINK (SHARE IT FROM CLAUDE) PLUS THE PARTY CODE.':'ONLINE PARTIES ONLY WORK ON THE SHARED PAGE LINK WHILE SIGNED IN. SOLO IS AVAILABLE.'}</p>`}
function hyClose(){$('hy').classList.add('hide')}
async function hyStart(mode){let code='',rm=null;
 if(mode==1)code=[...Array(5)].map(()=>'ABCDEFGHJKMNPQRSTUVWXYZ23456789'[r(0,30)]).join('');
 if(mode==2){code=($('hycode').value||'').toUpperCase().replace(/[^A-Z0-9]/g,'').slice(0,8);if(code.length<3){$('hyerr').textContent='ENTER A PARTY CODE FIRST';return}}
 if(mode){if(!HY.rm){$('hyerr').textContent='PARTIES UNAVAILABLE HERE';return}try{rm=await HY.rm.join('hy-'+code.toLowerCase())}catch(e){$('hyerr').textContent='COULD NOT JOIN PARTY ('+((e&&e.code)||'ERROR')+')';return}}
 const s=load(),orig=g;g=s?JSON.parse(JSON.stringify(s)):{f:0,k:0,hp:60,max:60,lv:1,xp:0,pot:3,w:0,a:0,iw:[0],ia:[0],nw:0};if(!g.iw){g.iw=[0];g.ia=[0];g.w=0;g.a=0}g.nw=g.nw||0;g.hp=g.max;g.pot=Math.max(g.pot,3);
 const hh=Math.round((3+W[g.w][1]+1.5)*5);HY={on:1,dm:Array(9).fill(0),seen:{},room:rm,rm:HY.rm,code,HH:hh,myHH:hh,tg:0,over:0,nm:'HERO'+r(100,999),orig};
 if(rm)rm.onPeers(hyPeers);
 mon={e:'',n:'Hydra',hp:1,max:1,atk:0,boss:false};$('hy').classList.add('hide');$('home').classList.add('hide');$('ov').classList.add('hide');$('stage').classList.add('hyb');hyBuild();$('log').innerHTML='';log('NINE HEADS RISE FROM THE DEEP!');if(code)log('PARTY CODE: '+code);
 busy=false;ui();hyAim();hyDraw();hySync()}
function hyBuild(){const d=document.createElement('div');d.id='hyd';d.style.cssText='position:absolute;inset:0;z-index:3';
 d.innerHTML=`<div style='position:absolute;left:50%;bottom:0;transform:translateX(-50%);z-index:0'>${SP('B','#3a4a2a #1a2a12 #6a7a4a #f33 #3a4a2a'.split(' '),[],162)}</div>`+HN.map((h,i)=>`<div class='hh' id='hh${i}' data-i='${i}' style='left:${HPS[i][0]}%;top:${HPS[i][1]}px'>${SP('J',h[1].split(' '),[],72)}<div class='hbar'><i id='hb${i}'></i></div><small>${h[0]}</small></div>`).join('')+"<div id='hyi'></div>";
 $('stage').appendChild(d);d.querySelectorAll('.hh').forEach(e=>e.onclick=()=>{const i=+e.dataset.i;if(!hyDead(i)){HY.tg=i;hyAim();hyDraw()}})}
function hyAim(){const e=$('hh'+HY.tg);if(!e)return;const c=cc(e.querySelector('img')),m=$('mon');m.style.left=c[0]+'px';m.style.top=(c[1]-60)+'px'}
function hyDraw(){HN.forEach((h,i)=>{const e=$('hh'+i);if(!e)return;const rem=Math.max(0,HY.HH-hyTot(i));$('hb'+i).style.width=rem/HY.HH*100+'%';e.classList.toggle('dead',rem<=0);e.classList.toggle('tg',i==HY.tg&&rem>0)});const ps=HY.room?HY.room.peers():[],f=p=>String(p.presence.nm||'HERO').replace(/[^A-Z0-9]/gi,'').slice(0,8);const hi=$('hyi');if(hi)hi.innerHTML=(HY.code?'PARTY '+HY.code:'SOLO')+ps.filter(p=>!p.isMe).map(p=>'<br>'+f(p)+' '+(typeof p.presence.mx=='number'&&p.presence.mx>0?Math.round(p.presence.hp/p.presence.mx*100)+'%':'')).join('')}
function hySync(){if(HY.room)HY.room.presence({dm:HY.dm,hh:HY.myHH,hp:g.hp,mx:g.max,nm:HY.nm})}
function hyPeers(ch){if(!HY.on)return;ch.peers.forEach(p=>{if(p.isMe)return;const d=p.presence.dm;if(Array.isArray(d)&&d.length==9){const o=HY.seen[p.peer]||(HY.seen[p.peer]=Array(9).fill(0));d.forEach((v,i)=>{if(typeof v=='number'&&v>o[i]&&v<1e9){const x=v-o[i];o[i]=v;const e=$('hh'+i);if(e){const c=cc(e);num('-'+(x|0),'#ffd84a',c[0]-14,c[1]-30);fx(e,'hit')}}})}if(typeof p.presence.hh=='number')HY.HH=Math.max(HY.HH,Math.min(p.presence.hh,1e6))});hyDraw();if(!HY.over&&hyAlive().length==0)hyWin()}
async function hyAtk(i){const el=$('hh'+i),a=cc(el.querySelector('img')),h=cc($('hero')),ps=[];
 el.animate([{transform:'translateX(-50%)'},{transform:'translateX(-50%) translateY(26px) scale(1.15)',offset:.4},{transform:'translateX(-50%)'}],{duration:500,easing:'steps(5)'});await wait(260);
 if(i==0){for(let j=0;j<5;j++){ps.push(fly(E('🔥',40),[h[0]+(j-2)*26,-20],[h[0]+(j-2)*26,h[1]],380,40));await wait(90)}}
 else if(i==1){for(let j=0;j<5;j++){ps.push(fly(E('❄️',36),a,[h[0],h[1]-8+j*4],420,36,'fan',j,5));await wait(90)}}
 else if(i==2){for(let j=0;j<3;j++){ps.push(fly(E('🧪',40),a,[h[0]+j*8,h[1]],420,40,'arc'));await wait(120)}}
 else if(i==3){for(let j=0;j<3;j++){bolt([h[0]+(j-1)*36,h[1]]);await wait(180)}fx($('flash'),'on')}
 else if(i==4){slash(h,true);boom(h,'#ff4040',10,60);await wait(250)}
 else if(i==5){ring([a[0],a[1]+40],'#fff');for(let j=0;j<5;j++){ps.push(fly(DUST,[a[0],h[1]+24],[h[0],h[1]+24],420,24));await wait(70)}}
 else if(i==6){for(let j=0;j<3;j++){ps.push(fly(E('🌊',48),a,[h[0],h[1]],420,48));await wait(120)}}
 else if(i==7){for(let j=0;j<3;j++){ring(a,'#e07dff',7);await wait(160)}await wait(200)}
 else{beam(a,h,'#ffe14a',26);await wait(520)}
 await Promise.all(ps);boom(h,'#ffb347',10,60)}
async function hyAct(t){if(busy||HY.over)return;busy=true;ui();
 if(hyDead(HY.tg))HY.tg=hyAlive()[0];const i=HY.tg;hyAim();hyDraw();let guard=false;
 if(t=='a'||t=='h'){await atkAnim(t);if(t=='h'&&Math.random()>=.6){log('Your heavy strike misses!');num('MISS','#ccc',$('stage').offsetWidth/2-30,110)}else{const d=Math.round(t=='h'?dmg()*1.8:dmg());HY.dm[i]+=d;fx($('hh'+i),'hit');fx($('stage'),'shake',300);hitFx(t);const c=cc($('hh'+i));num((crit?'*':'')+d,t=='h'?'#ffb830':'#fff',c[0]-20,c[1]-30);log(`You hit the ${HN[i][0]} head for ${d}.${crit?' CRITICAL!':''}`);const ls=Math.round(d*W[g.w][4]);if(ls){g.hp=Math.min(g.max,g.hp+ls)}hySync()}}
 if(t=='d'){guard=true;log('You raise your guard.')}
 if(t=='p'){g.pot--;const h=Math.min(Math.round(g.max*.35),g.max-g.hp);g.hp+=h;num('+'+h,'#6ef07e',50,190);log(`You drink a potion: +${h} HP.`)}
 hyDraw();ui();await wait(450);
 if(hyAlive().length==0){hyWin();return}
 const al=hyAlive(),k=al[r(0,al.length-1)];await hyAtk(k);
 if(Math.random()<A[g.a][3]){log('You dodge the '+HN[k][0]+' head!');num('DODGE','#aef',40,170)}else{let d=Math.max(1,Math.round(g.max*(.07+.02*r(0,2))*(1+.1*(9-al.length)))-Math.round(A[g.a][1]*.4));if(guard)d=Math.ceil(d/2);g.hp-=d;fx($('hero'),'hurt');fx($('flash'),'on');fx($('stage'),'shake',300);num('-'+d,'#ff5a43',40,170);log(`The ${HN[k][0]} head hits you for ${d}.`)}
 if(g.hp<=0){g.hp=0;hySync();ui();await wait(400);ov("<div class='big'>💀</div><h2>YOU FELL</h2><p>THE OTHER HEADS FIGHT ON. RISE AGAIN AND KEEP GOING!</p><button onclick='hyRise()'>RISE AGAIN</button>");return}
 hySync();busy=false;ui()}
function hyRise(){g.hp=g.max;$('ov').classList.add('hide');busy=false;hySync();ui()}
async function hyWin(){if(HY.over)return;HY.over=1;busy=true;ui();
 for(let i=0;i<9;i++){const c=cc($('hh'+i));boom(c,'#ffd84a',10,60);ring(c,'#fff');await wait(150)}
 fx($('flash'),'on');await wait(300);
 const gw=GW0+2,ga=GA0+2,nw=[];if(!g.iw.includes(gw)){g.iw.push(gw);nw.push(WE(gw,64))}if(!g.ia.includes(ga)){g.ia.push(ga);nw.push(AE(ga,64))}g.nw=(g.nw||0)+nw.length;g.hp=g.max;save();
 ov(`<div class='big'>🏆</div><h2>HYDRA SLAIN</h2><p>ALL 9 HEADS HAVE FALLEN!</p><div style='display:flex;justify-content:center'>${nw.join('')||'<p>YOU ALREADY OWN THE HYDRA GEAR.</p>'}</div><button onclick='hyDone()'>CONTINUE</button>`)}
function hyDone(){$('ov').classList.add('hide');home()}
function hyLeave(){if(!HY.on)return;HY.on=0;try{if(HY.room)HY.room.leave()}catch(e){}HY.room=null;const d=$('hyd');if(d)d.remove();$('stage').classList.remove('hyb');const m=$('mon');m.style.left='';m.style.top='';g=HY.orig;$('ov').classList.add('hide')}
const act0=act;act=function(t){return HY.on?hyAct(t):act0(t)};
const ui0=ui;ui=function(){ui0();if(HY.on)$('fn').textContent='BOSS MODE - NINE-HEADED HYDRA'};
const home0=home;home=function(){if(HY.on)hyLeave();home0()};
RN.push('Infernal','Sovereign');TC.push('#ff4a2a','#ffd700');
const HW0=W.length;[['Hellfire Blade','🔥'],['Brimstone Axe','🪓'],['Demon Maul','🔨'],['Infernal Scythe','🌙'],['Hell Trident','🔱'],['Cursed Bow','🏹'],['Imp Fang','🦷'],['Chain Whip','⛓️']].forEach((x,i)=>W.push([x[0],140+i*3,13,CR[i],LF[i],x[1]]));
const HR0=W.length;W.push(['Cerberus Fang',165,13,.3,.15,'🦷'],['Beelzebub Scepter',170,13,.3,.3,'🪄']);
const SW0=W.length;W.push(['Hellfire Scepter',215,14,.4,.3,'🪄'],['Satan Trident',230,14,.45,.3,'🔱']);
const HA0=A.length;A.push(['Brimstone Plate',62,13,0,'🛡️'],['Infernal Robe',55,13,.35,'👘'],['Demon Scale',58,13,.1,'🐉']);
const SA0=A.length;A.push(['King of Hell Plate',95,14,.15,'👑'],['Hell King Cloak',80,14,.4,'🧥']);
Object.assign(AC,{'Brimstone Plate':'#a03020','Infernal Robe':'#6a1a5a','Demon Scale':'#8a1a1a','King of Hell Plate':'#2a0a08','Hell King Cloak':'#7a0a1a'});
WI.push(...W.slice(WI.length).map(x=>x[5]));AI.push(...A.slice(AI.length).map(x=>x[4]));
const RWH=f=>f>=27?HR0+f-27:RWL(f);
function tierN(f){const w=Math.floor(f/3),fi=f%3;if(!w)return Math.min(4,fi+r(0,1)+(fi==2&&Math.random()<.2?1:0));const T=w>=9?13:Math.min(11,4+w);return Math.random()<.35+fi*.2?T:(w>=9?11:T-1)}
function tierB(f){const w=Math.floor(f/3);return w>=9?13:w?Math.min(11,4+w):f+1}
function dropW(t){const ok=i=>!g.iw.includes(i)&&!isR(i)&&!(i>=HR0&&i<HR0+2)&&![12,14].includes(W[i][2]);for(let d=0;d<15;d++)for(const tt of d?[t-d,t+d]:[t]){const c=W.map((x,i)=>i).filter(i=>W[i][2]==tt&&ok(i));if(c.length){giveW(c[r(0,c.length-1)],1);return}}log('You have collected every weapon!')}
F.push(F[24],F[24]);
F.push(...[['Gates of Hell','Imp','Hellhound','Fire Fiend','Cerberus'],['Lava Pit','Succubus','Bone Devil','Brimstone Brute','Beelzebub'],['Throne of Satan','Archdemon','Chain Devil','Damned Soul','Satan']].map((x,i)=>{const L=27+i;return{n:x[0],m:[1,2,3].map(j=>['?',x[j],...st(L,j)]),b:['?',x[4],...(x[4]=='Satan'?[4200,125]:st(L,0,1))]}}));
WD.push({n:'Hell',c:['#8a2a1a','#5a1a10','#2a0a08','#ff4a2a']});
NA.push([['shoot','🔥',3,36,'wave'],['claw'],['shoot','☄️',3,40,'rain']]);
const _am2=ambient;ambient=function(w){_am2(w==9?2:w)};
Object.assign(MS,{'Imp':['R','#e33 #811 #fa3 #ff0 #611',[[15,9,1,4,'#e33'],[2,2,2,2,'#611'],[12,2,2,2,'#611']]],'Hellhound':['R','#4a2a2a #1a0a0a #f60 #ff0 #2a1010',[[4,8,8,1,'#fff'],[15,8,1,4,'#4a2a2a']]],'Fire Fiend':['G','#f40 #a10 #fc0 #ff0 #f60',[[3,0,2,3,'#fc0'],[11,0,2,3,'#fc0'],[7,0,2,2,'#fc0']]],'Succubus':['H','#e8a0c0 #8a2a6a #6a1a5a #ff3030 #3a0a2a',[[0,4,3,6,'#8a2a6a'],[13,4,3,6,'#8a2a6a'],[3,0,2,3,'#3a0a2a'],[11,0,2,3,'#3a0a2a']]],'Bone Devil':['H','#eed #999 #ddc #f30 #ddc',[[2,0,2,3,'#ddc'],[12,0,2,3,'#ddc'],[14,1,1,13,'#a50'],[12,0,5,2,'#ddd']]],'Brimstone Brute':['B','#a42 #521 #c63 #ff0 #fd0',[[3,8,1,4,'#fd0'],[12,8,1,4,'#fd0'],[2,0,2,3,'#fd0'],[12,0,2,3,'#fd0']]],'Archdemon':['D','#701 #300 #d42 #ff0 #111',[]],'Chain Devil':['H','#8a8a9a #444 #333 #f30 #222',[[2,6,3,1,'#bbb'],[11,6,3,1,'#bbb'],[2,9,1,3,'#bbb'],[13,9,1,3,'#bbb'],[6,9,4,1,'#bbb']]],'Damned Soul':['G','#8f8 #3a6 #cfc #000 #8f8',[]]});
Object.assign(BS,{'Cerberus':{t:'B',p:['#5a1a14','#2a0a08','#8a2a1a','#ffe94a','#2a0a08'],x:[[0,2,3,5,'#7a2a1a'],[13,2,3,5,'#7a2a1a'],[1,3,1,1,'#ffe94a'],[14,3,1,1,'#ffe94a'],[0,5,3,1,'#fff'],[13,5,3,1,'#fff'],[6,9,4,2,'#ff6a1a']]},'Beelzebub':{t:'W',p:['#4a5a1a','#1a2a0a','#9aaa3a','#ff3030','#2a1a0a'],x:[[3,0,10,2,'#c8a000'],[3,3,3,2,'#ff3030'],[10,3,3,2,'#ff3030'],[0,5,3,6,'#6a7a2a'],[13,5,3,6,'#6a7a2a']]},'Satan':{t:'H',s:180,p:['#c0201a','#6a0f0c','#2a0a08','#ffe94a','#1a0a08'],x:[[0,3,3,8,'#6a0f0c'],[13,3,3,8,'#6a0f0c'],[1,0,2,4,'#2a0a08'],[13,0,2,4,'#2a0a08'],[14,0,1,15,'#777'],[12,0,5,2,'#aaa'],[6,9,4,2,'#ff6a1a'],[4,5,8,2,'#2a0a08']]}});
Object.assign(BB,{'Cerberus':['multi',[['charge'],['shoot','🔥',5,44,'line']]],'Beelzebub':['multi',[['shoot','🦟',7,32,'wave'],['nova','#8aaa2a']]]});
const SPH=[[['shoot','🔥',6,40,'rain'],['quake']],[['bolt'],['shoot','☄️',4,48,'arc'],['nova','#ff4a2a']],[['nova','#ff2a10'],['shoot','🔥',7,44,'wave'],['beam','#ff3a1a'],['blink']]];
async function monAtk(){const PH=mon.n=='God'?GP:mon.n=='Satan'?SPH:null;if(PH){const f=mon.hp/mon.max,ph=f>.66?0:f>.33?1:2;if(mon.ph!==ph){mon.ph=ph;if(ph){fx($('flash'),'on');fx($('stage'),'shake',300);toast((mon.n=='God'?'GOD ':'SATAN ')+(ph==1?'RAGES!':'ASCENDS!'),mon.n=='God'?11:13);log(mon.n+(ph==1?' unleashes his power!':' reveals his final form!'))}}await doAtk(['multi',PH[ph]]);return}await doAtk(mon.boss?(BB[mon.n]||['quake']):NA[Math.floor(g.f/3)][(g.k+g.f)%3])}
function entry(){const m=$('mon'),b=mon.boss,god=mon.n=='God',sat=mon.n=='Satan';m.classList.toggle('god',god||sat);$('stage').classList.toggle('divine',god);$('stage').classList.toggle('hellp',sat);m.animate([{transform:'translateX(-50%) translateY(-90px)',opacity:0},{transform:'translateX(-50%) translateY(0)',opacity:1,offset:.7},{transform:'translateX(-50%) translateY(0)',opacity:1}],{duration:b?700:450,easing:'steps(6)'});setTimeout(()=>{const c=cc($('me'));boom([c[0],c[1]+60],'#e9d9a8',8,40);if(b)fx($('stage'),'shake',300);if(god||sat){fx($('flash'),'on');ring(c,sat?'#ff4a2a':'#fff6a0',8)}},b?450:300)}
function heroHTML(){const a=A[g.a],m=AC[a[0]]||'#999',pal=['#f1c27d',dk(m,.6),m,'#222',a[2]>=2?m:'#6b4423'],ex=(a[2]>=3?[[7,0,2,2,'#ff4040']]:[]).concat(g.king?[[4,0,1,2,'#ffd84a'],[7,0,2,2,'#ffd84a'],[11,0,1,2,'#ffd84a'],[4,1,8,1,'#ffd84a'],[7,1,2,1,'#ff3030']]:[]);
 return `<div style="position:relative;width:72px;height:72px">${SP('H',pal,ex,72)}<div style="position:absolute;right:-30px;top:8px;transform:rotate(25deg)">${WE(g.w,60)}</div></div>`}
async function coronation(){busy=true;const cs=$('cs');cs.innerHTML="<canvas id='csc'></canvas><div id='cst'></div><div id='csi'></div>";cs.classList.remove('hide');
 const cv=$('csc'),q=cv.getContext('2d'),w0=cv.width=cs.clientWidth,h0=cv.height=cs.clientHeight,tx=$('cst'),say=(t,ms)=>{tx.textContent=t;return wait(ms)},U=Math.max(6,Math.min(14,Math.floor(Math.min(w0,h0*.8)/20))),bx=w0/2,by=h0*.62;
 const ld=async h=>{const i=new Image();i.src=h.match(/src="([^"]+)"/)[1];await i.decode();return i},G=BS.Satan,si=await ld(SP(G.t,G.p,G.x,180)),a=A[g.a],mc=AC[a[0]]||'#999',hi=await ld(SP('H',['#f1c27d',dk(mc,.6),mc,'#222',a[2]>=2?mc:'#6b4423'],[],72));
 const oc=document.createElement('canvas');oc.width=oc.height=18;const oq=oc.getContext('2d');oq.drawImage(si,0,0);const px=oq.getImageData(0,0,18,18).data,P=[],EM=[...Array(70)].map(()=>({x:Math.random()*w0,y:Math.random()*h0,v:.6+Math.random()*1.6,s:2+Math.floor(Math.random()*3)*2,c:Math.random()<.5?'#ff7a1a':'#ffd84a'}));
 for(let y=0;y<18;y++)for(let x=0;x<18;x++){const i=(y*18+x)*4;if(px[i+3]>0)P.push({x:bx+(x-9)*U,y:h0*.36+(y-9)*U,c:`rgb(${px[i]},${px[i+1]},${px[i+2]})`,vx:(Math.random()-.5)*8,vy:-Math.random()*7-1,a:1})}
 let ph=0,cr=0,done=false;const t0=performance.now();
 (function loop(){if(done)return;const t=performance.now()-t0,gr=q.createLinearGradient(0,0,0,h0);gr.addColorStop(0,'#1a0505');gr.addColorStop(1,ph>1?'#7a1a0a':'#a02a10');q.fillStyle=gr;q.fillRect(0,0,w0,h0);
  EM.forEach(e=>{e.y-=e.v;if(e.y<-8){e.y=h0;e.x=Math.random()*w0}q.fillStyle=e.c;q.fillRect(e.x,e.y,e.s,e.s)});
  q.fillStyle='#ff6a1a';q.fillRect(0,h0*.84,w0,h0*.16);q.fillStyle='#ffb347';for(let k=0;k<w0;k+=U*3)q.fillRect(k+(t/80%(U*3)),h0*.84,U,U*.5);
  if(ph<2){P.forEach(p=>{if(ph<1){q.fillStyle=p.c;q.fillRect(p.x+(Math.random()-.5)*4,p.y+(Math.random()-.5)*4,U,U)}else if(p.a>0){p.x+=p.vx;p.y+=p.vy;p.vy+=.12;p.a-=.006;q.globalAlpha=Math.max(0,p.a);q.fillStyle=p.c;q.fillRect(p.x,p.y,U,U);q.globalAlpha=1}})}
  else{q.fillStyle='#4a0f0f';q.fillRect(bx-5*U,by-11*U,10*U,13*U);q.fillStyle='#6a1a1a';q.fillRect(bx-4*U,by-10*U,8*U,11*U);q.fillStyle='#2a0808';for(let k=0;k<5;k++)q.fillRect(bx-5*U+k*2.4*U,by-14*U,1.3*U,3*U);q.fillRect(bx-7*U,by-4*U,2*U,6*U);q.fillRect(bx+5*U,by-4*U,2*U,6*U);q.fillRect(bx-6*U,by,12*U,2*U);q.fillRect(bx-9*U,by+2*U,18*U,U);
   q.imageSmoothingEnabled=false;q.drawImage(hi,bx-5*U,by-9.6*U,10*U,10*U);
   const cy=-40+(by-9.9*U+40)*Math.min(1,cr);q.fillStyle='#ffd84a';q.fillRect(bx-2*U,cy,4*U,.9*U);[-2,-.4,1.1].forEach(o=>q.fillRect(bx+o*U,cy-1.4*U,.9*U,1.5*U));q.fillStyle='#ff3030';q.fillRect(bx-.4*U,cy+.1*U,.8*U,.6*U)}
  requestAnimationFrame(loop)})();
 await say('SATAN FALLS TO HIS KNEES...',2200);
 cv.animate([{filter:'brightness(5)'},{filter:'none'}],{duration:700});ph=1;
 await say('THE FLAMES OF HELL BOW TO YOU.',2400);
 ph=2;await say('THE LEGIONS OF HELL KNEEL BEFORE THE THRONE...',2200);
 tx.textContent='A CROWN OF FIRE DESCENDS...';for(let s=1;s<=20;s++){cr=s/20;await wait(110)}
 cv.animate([{filter:'brightness(5)'},{filter:'none'}],{duration:900});
 await say('YOU ARE CROWNED KING OF HELL!',3000);
 tx.textContent='';const box=$('csi');
 for(const [k,id] of [[0,SW0],[0,SW0+1],[1,SA0],[1,SA0+1]]){const own=k?g.ia:g.iw;if(!own.includes(id))own.push(id);const x=(k?A:W)[id];box.insertAdjacentHTML('beforeend',`<div class='cc' style='box-shadow:0 0 16px #ffd700'>${k?AE(id,96):WE(id,96)}<b>${x[0].toUpperCase()}</b><small>SOVEREIGN - ${k?'-'+x[1]+' DMG':'+'+x[1]+' ATK'}</small></div>`);await wait(1000)}
 g.nw=(g.nw||0)+4;await say('LONG LIVE THE KING OF HELL.',1500);
 box.insertAdjacentHTML('beforeend',"<button id='csb' style='width:100%;padding:12px;margin-top:6px;font-size:11px'>CLAIM THE THRONE</button>");
 await new Promise(res=>$('csb').onclick=res);
 done=true;cs.classList.add('hide');cs.innerHTML='';g.king=1;g.f=0;g.k=0;g.hp=g.max;save();home()}
async function act(t){
 if(busy)return;busy=true;ui();let guard=false;
 const sw=()=>atkAnim(t);
 if(t=="a"||t=="h"){
  await sw();
  if(t=="h"&&Math.random()>=.6){log("Your heavy strike misses!");num("MISS","#ccc",$("stage").offsetWidth/2-30,110)}
  else{const d=t=="h"?Math.round(dmg()*1.8):dmg();mon.hp-=d;fx($("mon"),"hit");hitFx(t);fx($("stage"),"shake",300);
   num((t=="h"?"💥":"")+d,t=="h"?"#ffb830":"#fff",$("stage").offsetWidth/2-20,100);log(`You hit the ${mon.n} for ${d}.${crit?" CRITICAL!":""}`);const ls=Math.round(d*W[g.w][4]);if(ls){g.hp=Math.min(g.max,g.hp+ls);log(`You drain ${ls} HP.`)}}
 }
 if(t=="d"){guard=true;log("You raise your guard.")}
 if(t=="p"){g.pot--;const h=Math.min(40,g.max-g.hp);g.hp+=h;num("+"+h,"#6ef07e",50,190);log(`You drink a potion: +${h} HP.`)}
 ui();await wait(450);
 if(mon.hp<=0){await win();return}
 await monAtk();
 if(Math.random()<A[g.a][3]){log(`You dodge the ${mon.n}'s attack!`);num("DODGE","#aef",40,170);busy=false;ui();return}
let d=Math.max(1,mon.atk+r(0,2)-A[g.a][1]);if(guard)d=Math.ceil(d/2);
 if(mon.boss&&Math.random()<.2){d=Math.round(d*1.6);log(`The ${mon.n} unleashes a devastating blow!`)}
 g.hp-=d;fx($("hero"),"hurt");fx($("flash"),"on");fx($("stage"),"shake",300);num("-"+d,"#ff5a43",40,170);log(`The ${mon.n} hits you for ${d}.`);
 if(g.hp<=0){g.hp=0;ui();await wait(500);ov(`<div class="big">💀</div><h2>YOU DIED</h2><p>Slain on floor ${g.f+1} by the ${mon.n}. You keep all your gear, levels and potions.</p><button onclick="retry()">RISE AGAIN</button>`);return}
 busy=false;ui()}
async function win(){
 fx($("mon"),"die",700);log(`✔ You defeated the ${mon.n}!`);await wait(700);$("mon").style.display="none";
 g.xp+=mon.boss?100:50;const need=g.lv;g.lv++;g.max+=8;g.hp=Math.min(g.max,g.hp+8);log(`Level up! Max HP ${g.max}.`);
 if(Math.random()<.4){g.pot++;log("You found a potion! 🧪")}
 const f=g.f;
 if(mon.boss){
  if(mon.n=='God'){await finale();return}if(f==F.length-1){await coronation();return}if(0){clearSave();ui();await wait(400);ov(`<div class="big">🏆</div><h2>VICTORY</h2><p>The Allfather falls and the gods themselves bow to you. You reached level ${g.lv} wielding ${W[g.w][0]}.</p><button onclick="start()">PLAY AGAIN</button>`);return}
  giveW(RWH(f));loot(1,tierB(f));
 }else{dropW(tierN(f));if(Math.random()<.4)loot(1,tierN(f))}
 ui();await wait(1400);
 if(mon.boss){if(g.f%3==2)await portal();g.f++;g.k=0;const h=Math.round(g.max*.4);g.hp=Math.min(g.max,g.hp+h);log(`You descend and rest: +${h} HP.`)}else g.k++;
 spawn()}
const pk=(x,k)=>k?(x[3]?Math.round(x[3]*100)+"% dodge":""):(x[3]?Math.round(x[3]*100)+"% crit":x[4]?Math.round(x[4]*100)+"% drain":"");
function openBag(){g.nw=0;drawBag();$("bg").classList.remove("hide");ui()}
function closeBag(){$("bg").classList.add("hide")}
function drawBag(){
 const row=(k,id,eq)=>{const x=(k?A:W)[id],t=x[2];return `<div class="it${eq?" eq":""}" style="--c:var(--t${t})" data-k="${k}" data-i="${id}">${k?AE(id,48):WE(id,48)}<div><b>${x[0]}</b><small>${RN[t]} - ${k?"-"+x[1]+" dmg":"+"+x[1]+" atk"} ${pk(x,k)}</small></div><span>${eq?"EQUIPPED":"EQUIP"}</span></div>`};
 $("bgc").innerHTML=`<div class="prow"><span>ATK ${3+W[g.w][1]} - DEF ${A[g.a][1]}</span><span><button onclick="closeBag();openFz()" style="padding:6px 10px;font-size:8px">FUSE</button> <button onclick="closeBag()" style="padding:6px 10px;font-size:8px">CLOSE</button></span></div><p>TAP AN ITEM TO EQUIP IT</p><h3>WEAPONS</h3>${[...g.iw].sort((a,b)=>W[b][1]-W[a][1]).map(i=>row(0,i,i==g.w)).join("")}<h3>ARMOUR</h3>${[...g.ia].sort((a,b)=>A[b][1]-A[a][1]).map(i=>row(1,i,i==g.a)).join("")}`;
 document.querySelectorAll("#bgc .it").forEach(e=>e.onclick=()=>{const k=+e.dataset.k,i=+e.dataset.i;if(k)g.a=i;else g.w=i;save();drawBag();ui()})}
function loot(kind,t){
 const L=kind?A:W,own=kind?g.ia:g.iw,c=L.map((x,i)=>i).filter(i=>L[i][2]==t&&!(!kind&&isR(i)));
 const id=c[r(0,c.length-1)],it=L[id],ic=kind?it[4]:it[5];
 if(own.includes(id)){log(`Found ${it[0]} again - you already own one.`);return}
 own.push(id);g.nw=(g.nw||0)+1;toast(`${kind?AE(id,40):WE(id,40)} ${it[0]}<br>${RN[t]}! In your bag`,t);log(`⭐ Loot: ${it[0]} (${RN[t]}). Added to bag!`)}
function loot0(kind,t){
 const L=kind?A:W,cur=kind?g.a:g.w,it=L[t],ic=(kind?AI:WI)[t];
 if(t>cur){kind?g.a=t:g.w=t;toast(`${E(ic,28)} ${it[0]}<br>${RN[t]}!`,t);log(`⭐ Loot: ${it[0]} (${RN[t]}). Equipped!`)}
 else log(`Found ${it[0]}, but yours is better.`)}
mon={e:"",n:"",hp:1,max:1};g={f:0,k:0,hp:60,max:60,lv:1,xp:0,pot:3,w:0,a:0};busy=true;ui();home();
</script></body></html>

dungeon game
