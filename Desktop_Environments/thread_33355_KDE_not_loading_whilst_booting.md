---
title: "KDE not loading whilst booting"
date: 2005-05-10
forum: Desktop Environments
---

### Post by adambaz on 2005-05-10
I recently changed to kubuntu from ubunto, and upon booting tonight it goes straight into the console and asks for my login name and password, but wont let me into kubuntu.

I have tried:
Startx, but this doesnt work.
sudo /etc/init.d/kdm start, but this also doesnt boot into KDE.
Control + Alt + F6 doesnt either.

Can anybody please help me ?

Thanks in advance

AdamBaz

---

### Post by adambaz on 2005-05-10
It's probably worth mentioning that i've recently installed a new graphics card (radeon 9800 Pro)

Cheers.

---

### Post by Kurse on 2005-05-10
Did you reconfigure X for your new graphics card? KDE cant start if X wont run because you havent updated your configuration.

---

### Post by adambaz on 2005-05-10
[QUOTE=Kurse]Did you reconfigure X for your new graphics card? KDE cant start if X wont run because you havent updated your configuration.[/QUOTE]
 how would i go about reconfiguring X?

cheers.

---

### Post by Kurse on 2005-05-10
The configuration file for X is /etc/X11/xorg.conf

The log file that will tell you what problems X is having is /var/log/Xorg.0.log

I would guess that your last video card was not ATI, or an older ATI card that used a different driver. This is just a guess, it could be other problems.

---

