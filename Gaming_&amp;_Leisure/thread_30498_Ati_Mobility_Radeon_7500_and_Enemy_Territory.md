---
title: "Ati Mobility Radeon 7500 and Enemy Territory"
date: 2005-04-28
forum: Gaming &amp; Leisure
---

### Post by deviant03 on 2005-04-28
Just installed Hoary and need some help with ET. ET will only start under fluxbox when I  type et in terminal. I try the same thing under gnome and all I get is a blank screen. Any ideas on how to fix this?

Second thing is I have a Thinkpad T30 with a Ati mobility radeon 7500 which fglrx dosent seem to support. Is there anyway I can boost the 3D performance of my card?  I am getting about 830fps from glxgears thanks to the tweaks by NTolerance in this thread - [http://ubuntuforums.org/showthread.php?t=29990](http://ubuntuforums.org/showthread.php?t=29990) but ET is still barely playable. Any help would be appreciated.

---

### Post by Locomorto on 2005-04-29
[QUOTE=deviant03]Just installed Hoary and need some help with ET. ET will only start under fluxbox when I  type et in terminal. I try the same thing under gnome and all I get is a blank screen. Any ideas on how to fix this?

Second thing is I have a Thinkpad T30 with a Ati mobility radeon 7500 which fglrx dosent seem to support. Is there anyway I can boost the 3D performance of my card?  I am getting about 830fps from glxgears thanks to the tweaks by NTolerance in this thread - [http://ubuntuforums.org/showthread.php?t=29990](http://ubuntuforums.org/showthread.php?t=29990) but ET is still barely playable. Any help would be appreciated.[/QUOTE]
 Yes, check out this: [http://www.ubuntuguide.org/#configuresoundproperly](http://www.ubuntuguide.org/#configuresoundproperly)
, you can look at the DRI
It worked great for me, the other trick didn't do anything for me :(.

As for your second question, you can look at the DRI drivers, i believe they work for your card.

---

### Post by deviant03 on 2005-04-29
Ok, the sound fix worked. As for the DRI drivers I have Load	"dri" in my xorg.conf under the Module section already, does that mean it is already enabled?

---

### Post by Locomorto on 2005-04-30
[QUOTE=deviant03]Ok, the sound fix worked. As for the DRI drivers I have Load	"dri" in my xorg.conf under the Module section already, does that mean it is already enabled?[/QUOTE]
 It should be, and considering that you can run all the benchmarks, but 800 FPS is very low, so it could just be your hard ware. Can you run Enemy Territory in windows? (assuming you still have it, used ET in windows on that machine)

Well i had a look at that tweak he siad he got 2000+ FPS with your laptop (i only get ~1500 btw).

---

### Post by deviant03 on 2005-04-30
When I was on XP I was able to run MOHAA and ET on low settings perfectly fine so its definitely a problem with getting it to run properly on linux. Do you know of any more tweaks I could try? Thanks for your help btw.

---

### Post by deviant03 on 2005-04-30
Also if you can would you please post your xorg.conf, I just wanted to compare it to mines to see if Im missing any options that should be enabled  ;-)

---

