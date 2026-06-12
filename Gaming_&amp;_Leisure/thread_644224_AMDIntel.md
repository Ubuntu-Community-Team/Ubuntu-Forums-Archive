---
title: "AMD/Intel"
date: 2007-12-18
forum: Gaming &amp; Leisure
---

### Post by metricben on 2007-12-18
Sorry if this isn't in the right forum.  Feel free to move.

I am building a new Ubuntu Box, and am trying to decide which way to go: AMD or Intel.  I have found suitable dual-core processors on Microdirect (a cheap UK-based site I use) and would appreciate any input or advice:
Intel: [one]("http://www.microdirect.co.uk/(17743)Intel-CPU-Pentium-DualCore-E2140-2x160GHz.aspx") [two]("http://www.microdirect.co.uk/(17744)Intel-CPU-Pentium-DualCore-E2160-2x180GHz.aspx")
AMD: [one]("http://www.microdirect.co.uk/(15380)AMD-CPU-AM2-Athlon-64-3800-Retail-Dual-core.aspx") [two]("http://www.microdirect.co.uk/(16094)AMD-CPU-AM2-Athlon-64-Dual-Core-4200-Retail.aspx")

The main things I am looking for are:
[LIST]
[*]Price
[*]Performace (the AMDs look better to me)
[*]Cost of corresponding MOBO
[*]Overclockability (Intel wins on this I think)
[/LIST]

Thanks,
Ben

---

### Post by piratesmack on 2007-12-18
I'd go with one of those AMD's

They're more powerful than the 2 Intels, and they have a cool feature called "Cool 'n' Quiet" (Which Linux takes advantage of)

Cool 'n' Quiet is just a feature where if your processor isn't being used very intensively, it underclocks itself to make it run cooler and quieter. When you run something that requires more power (Like a game), it will automatically clock the processor back up to normal speed so you won't suffer any performance loss.

---

### Post by a12ctic on 2007-12-18
for gaming, it doesn't matter. As long as its dual core, you shouldnt be cpu limited. Just get a beefy graphics card. If your going for an intel chip at least shoot for a C2D.

---

### Post by metricben on 2007-12-19
OK, thanks for replies.  I will probably go AMD.

Three more questions:

Where can I find an Nvidia benchmark list featuring the 7000/8000 series?  I want a place with a simple table showing FPS for each card if possible.  Any suggestions?

I am trying to connect a D-link router to my home network so that I can connect my Windows and Linux box to the web at the same time.  I have connected my two PCs to two LAN ports, but should I connect my main router to the WAN posrt or another LAN?

I want to run a dual screen setup on Linux but sometimes use Windows on one of the screens.  I believe I can do this with Synergy and a simple KVM, but how simple is it to change Ubuntu from dual to single screen?  X restart?  Or could I just use only one screen while using Windows on the other?

How configurable in Compiz Fusion with  dual screens?

Thanks
Ben

---

### Post by Zylar on 2007-12-19
I like AMD too.

Tomshardware.com has a comparison table that you can use for video benchmarks:

[http://www23.tomshardware.com/graphics_2007.html](http://www23.tomshardware.com/graphics_2007.html)

Does your main router only have 1 lan port?  I would suggest using a switch then, instead of a 2nd router.  A 5-port switch you can get for as little as $15usd.  Plug the 1 lan port of your router into the switch along with the 2 ethernet cables from the PCs, all done.  Plus no headaches if you ever want remote access to your home systems or want to host any web servers/services.  Otherwise, yeah, lan on main router goes to wan on 2nd router, to prevent dhcp/gateway issues.

As far as the dual monitors/kvm situation, I can't help there, sorry.  I have seen dual monitors with Compiz-Fusion on youtube.com, but no personal experience.

Good luck,

---

### Post by metricben on 2007-12-19
Thanks for Toms Hardware link.  I've been there before,  just forgot URL :P

Anyone on Compiz Fusion?
Do you think desktop cube effect wouls work independently on both monitors?

Thanks

---

### Post by Sockerdrickan on 2007-12-19
The new AMD ones are cool

---

### Post by rsambuca on 2007-12-19
Unless you are going to get a Core 2 Duo, which neither of those options are, then definitely go with the AMD line.  You will get much better performance for the price with the AMD's.  

If you decide to upgrade further though and go with the Core 2 Duo, then the performance is much better than anything AMD currently has.

---

### Post by chewearn on 2007-12-19
I have a dual screen set-up on nvidia graphics.  Once it is fully set-up, everything was wonderful, but to get to that point was a major pita. Despite better dual screen configuration available in gutsy, I found it to be unworkable. Using nvidia-settings makes thing much better, but it is still a long way to go to match what Windows can do.

Running compiz-fusion in Ubuntu (Gnome) with two separate screens, you will likely run into this problem:
[http://ubuntuforums.org/showthread.php?t=536045](http://ubuntuforums.org/showthread.php?t=536045)

There is a workaround; but I finally have to disable compiz because of random hard lock-ups.  The lock-up seemed to occur after some hours playing video in the second screen.  Maybe you have better luck.

Other than that, compiz cube (and other effects) worked great.

---

### Post by Tadock on 2007-12-19
If your on a budget get an AMD better value I think. But, if you got a crap ton of cash buy a Intel

---

### Post by rsambuca on 2007-12-19
> **AstalaVista said:**
> I have a dual screen set-up on nvidia graphics.  Once it is fully set-up, everything was wonderful, but to get to that point was a major pita. Despite better dual screen configuration available in gutsy, I found it to be unworkable. Using nvidia-settings makes thing much better, but it is still a long way to go to match what Windows can do.

Running compiz-fusion in Ubuntu (Gnome) with two separate screens, you will likely run into this problem:
[http://ubuntuforums.org/showthread.php?t=536045](http://ubuntuforums.org/showthread.php?t=536045)

There is a workaround; but I finally have to disable compiz because of random hard lock-ups.  The lock-up seemed to occur after some hours playing video in the second screen.  Maybe you have better luck.

Other than that, compiz cube (and other effects) worked great.

Was your post meant for this thread?

---

### Post by chewearn on 2007-12-19
> **rsambuca said:**
> Was your post meant for this thread?

I'm replying to the OP questions in post #4.

---

### Post by rsambuca on 2007-12-19
> **AstalaVista said:**
> I'm replying to the OP questions in post #4.

Ahh, missed that, sorry!

---

### Post by rsambuca on 2007-12-19
Regarding the dual monitors, though, I found it very easy to set up.  All it takes is adding 4 lines to your xorg.conf and you are done.  It seemed to be a lot neater than when you let nvidia-settings handle it.

---

### Post by metricben on 2007-12-19
Thanks for replies.   From what I hear it COULD potentially be very easy to set up dual monitors, although I am still concerned about the performance loss.  It will be great when we can play all games multi-screen.  RTS could have a separate window for eco, chat, units and loads of other stuff that you cant fit into one monitor. :P

---

### Post by chewearn on 2007-12-20
> **rsambuca said:**
> Regarding the dual monitors, though, I found it very easy to set up.  All it takes is adding 4 lines to your xorg.conf and you are done.  It seemed to be a lot neater than when you let nvidia-settings handle it.

In my case:
1. it needs than 4 lines of change in xorg.conf (I counted at least 20 lines).
2. no clue what needs to be changed when doing it first time. (second and subsequent time, of course, just copy the old working xorg.conf back).
3. the new "Screens and Graphics" in Gutsy was suppose to help in this, so it takes maybe half an hour to mess with it, and found it doesn't work the way you want
4. when changing xorg.conf, it needs your full attention, you can't be doing sometime else on your ubuntu in the mean time, because you need to restart x each time you try some changes in xorg.conf

---

### Post by rsambuca on 2007-12-20
> **AstalaVista said:**
> In my case:
1. it needs than 4 lines of change in xorg.conf (I counted at least 20 lines).
2. no clue what needs to be changed when doing it first time. (second and subsequent time, of course, just copy the old working xorg.conf back).
3. the new "Screens and Graphics" in Gutsy was suppose to help in this, so it takes maybe half an hour to mess with it, and found it doesn't work the way you want
4. when changing xorg.conf, it needs your full attention, you can't be doing sometime else on your ubuntu in the mean time, because you need to restart x each time you try some changes in xorg.conf

All I always add is the following lines:

> Option "TwinView" "True"
Option "TwinViewOrientation" "RightOf"   
Option "UseEdidFreqs" "True"
Option "MetaModes" "1280x1024,1280x1024; 1024x768,1024x768"
The EDID line isn't really required, and the metamodes can be edited to your specific situation.

When I used nvidia-settings it added a whole bunch of lines which I didn't understand.  It didn't seem to run quite right, so I changed back to this old-school method, which works on my rig.

---

