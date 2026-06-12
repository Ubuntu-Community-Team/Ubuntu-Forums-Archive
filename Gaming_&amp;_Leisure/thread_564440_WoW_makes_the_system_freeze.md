---
title: "WoW makes the system freeze"
date: 2007-10-01
forum: Gaming &amp; Leisure
---

### Post by bogeangles on 2007-10-01
Hi, 

I wanted to make Wow with wine on my laptop, followed the howto and everithing seemed to be just fine. But the system freeze completely after I enter the word. 
I tried to disable the sound from WINE, but it didn't helped.
I tried to launch it with "wine WoW.exe -d3d" but the result was the same(system freeze).

if I dont enter the world, the sound seems to be ok.

I have an T60 IBM laptop, ATI radeon mobility  X1300, 1G ram, wine 0.9.45 

I'll go back to read the 85 pages of the howto, in hope i'll find something useful there...

---

### Post by mastersenser on 2007-10-01
If your Desktop Effects is enabled, try to disable it.

Also don't forget the -OpengGL commandline.

---

### Post by bogeangles on 2007-10-02
I made it work, doing the following things:
I put in Interface folder the following addon: 
1.ApplyToForehead 
2. added the following lines in my xorg.conf
Section "Device"
    Identifier "aticonfig-Device[0]"
    Driver "fglrx"
 [COLOR="Red"]   Option "Capabilities" "0x00000800"
    Option "UseFastTLS" "off"
    Option "KernelModuleParm" "locked-userpages=0"[/COLOR]
EndSection
. 

Now it works, 25-30 FPS, but with a huge memory consumption, top shows 2.7 G...

---

### Post by bogeangles on 2007-10-04
another annoying thing is that if I alt tab from the game, i lose  the sound. :(

---

### Post by hikaricore on 2007-10-04
> **bogeangles said:**
> another annoying thing is that if I alt tab from the game, i lose  the sound. :(

This has been an issue since WINE 0.9.43.  You should be able to fix it by toggling "sound in background" though I havn't had trouble in 0.9.46 either way.

---

