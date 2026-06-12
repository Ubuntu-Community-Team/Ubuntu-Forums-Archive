---
title: "[SOLVED] Enabled dual monitor; now can't login"
date: 2007-10-20
forum: Desktop Environments
---

### Post by punky on 2007-10-20
I just installed Ubuntu gutsy and tried to enable the second monitor. 

Everything looked OK in the settings and I had to restart. Got to the login screen, and the main monitor is blank, and the secondary monitor has the ubuntu login background, but no screen. If I move the cursor onto the secondary desktop it appears, but corrupted. I've tried logging in 'blind', but that doesn't work. I've also tried removing both monitors and trying them individually in both ports, still nothing.

Anyone know how to correct it?

Many thanx in advance.

---

### Post by digital_exhaust on 2007-10-20
What graphics driver are you using, how did you install it and what type of video card do you have?

---

### Post by repawn on 2007-10-20
I had a similar problem with one of my computers - I had to log in in safe mode (hit escape as the grub menu is loading - then choose safe mode.) Login to the terminal and then cd /etc/X11 - run a ls to see what you have in the directory - look for your xorg.conf and then look to see if you have any backups - if so you can make a backup of the current non-working xorg.conf and then replace it with a older backup. Hope it helps - feel free to ask for clarification.

---

### Post by punky on 2007-10-20
> **repawn said:**
> I had a similar problem with one of my computers - I had to log in in safe mode (hit escape as the grub menu is loading - then choose safe mode.) Login to the terminal and then cd /etc/X11 - run a ls to see what you have in the directory - look for your xorg.conf and then look to see if you have any backups - if so you can make a backup of the current non-working xorg.conf and then replace it with a older backup. Hope it helps - feel free to ask for clarification.

Awesome mate, thanx so much :) I was worried there wouldn't be a backup as I altered it through the GUI, but there was a .1 file, replaced it and logged in fine. Thanx again mate.

> **digital_exhaust said:**
> What graphics driver are you using, how did you install it and what type of video card do you have?

Cheers mate. I have a Radeon x1600xt I'm using xgl and the proprietary ATI it told me to enable after I installed gutsy.

I've now noticed the test button which I am making use of. Can't seem to find any config though which allows me to use both monitors. So I think I need to look at  3rd party apps like Xinerama or [this](http://ubuntuforums.org/showthread.php?t=581947)

Thanx again guys :KS:

---

