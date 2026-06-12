---
title: "The bottleneck.......CPU or GFX?"
date: 2008-03-03
forum: Gaming &amp; Leisure
---

### Post by phillips321 on 2008-03-03
Hi guys,

I'm trying to figure out what's causing my bottleneck in counter strike source.

2.8 GHz Pentium 820D
3GB Ram
7900GS 256MB

On a 60 man server at 1920x1200 I'm getting on average 30-40fps but this sometimes drops to 20fps which is a killer for both me and the character im playing in the game.

I tested my friends 8800GTS 320MB today, I don't think it made much of a difference, in fact I don't think i saw any increase at all.

Could my CPU possibly be struggling with all of the physics, player count, etc....? What would be the best way to identify the bottle neck.

Cheers guys

---

### Post by Melcar on 2008-03-03
Yes, it's probably your CPU that's slowing down the system.

---

### Post by happyhamster on 2008-03-03
Agreed, looks like the cpu is the culprit.

> **phillips321 said:**
> I tested my friends 8800GTS 320MB today, I don't think it made much of a difference, in fact I don't think i saw any increase at all.Which is pretty conclusive evidence. The other way of testing is running the game at a lower resolution. If you get the same kind of framerates, then it's more proof that the cpu is holding you back.

---

### Post by phillips321 on 2008-03-03
hmm, going to have to look into getting more out of my current cpu (overclocking) or possibly tweaking the game to be less of a strugle for the cpu.

Current memory says 533MHz on the side, if i upgrade my mobo and cpu to a E4500(800MHz fsb) will it cope? My current cpu has 800MHz fsb so i guess my memory should still be compatible?

cheers guys

---

### Post by keltren on 2008-03-06
Counter Strike is running over wine right? 
With pretty much any app running over wine the cpu is going to be the bottleneck, simply due to necessary translation of system calls taking place.
Going from an e6300 to a e8400 doubled my framerate in WoW with all else being equal (when I switched the cpu I still had a gf7900gs - now using a gf9600gt but at least for wow under linux that didn't make much of a difference anymore so I guess even an e8400 is still the bottleneck for that particular app.)
A newer gfx card mostly helps if you want to run games that use HDR, AA or other shader intensive processes, as the new cards can run these with little or now impact - i.e. HDR usually cripples performance on a gf7900, but on a gf9600 it's got next to no performance impact.

I'm not sure how big of an upgrade the e4500 is going to be though...maybe wait for advice from other users first as to how much of a difference it'll make - I'm not familiar with intel cpu's before the core2duo's myself.

---

### Post by desicratn on 2008-03-06
Your CPU is absolutely the bottleneck.

[http://www23.tomshardware.com/cpu_2007.html?modelx=33&model1=899&model2=882&chart=424](http://www23.tomshardware.com/cpu_2007.html?modelx=33&model1=899&model2=882&chart=424)

Tomshardware is your friend. NOTE the 4500 isnt on that chart however the 4300 is and they are similar chips( 1.8 vs 2.2 same cache[2M] and Front Side Bus :800).Your current chip is getting roughly 60 FPS in the demo noted on Toms. The Newegg price on a e4500 is 130$(which is getting roughly 79 fps on the demo). A chip like the e6550(2.2ghz 1333FSB and 4MB Cache) is an AWESOME chip that  is only 170$ and is getting like 104 FPS for 40$ more...) The 6550 is a solid performer without breaking the bank, depending on your budget.Hard to beat without going Quad core,HOWEVER it is a newer 1333 FSB C2D chip and may not work with older socket 775 mobos,check to see what chips your Mobo supports. 

And yes you can run a 800/1066/ or 1333 FSB chip with  DDR2 533 it just changes the FSB to Mem  clock ratio. If I  had a 1066 FSB chip with 533 ram the ratio would be 1:2 etc...However with the dropping costs of DDR2 800, you can find 2 GB 4-4-4-12 DDR2-800 for 50$ and under with rebates.Good RAM is cheap right now, look @ Newegg or Tiger Direct.

---

