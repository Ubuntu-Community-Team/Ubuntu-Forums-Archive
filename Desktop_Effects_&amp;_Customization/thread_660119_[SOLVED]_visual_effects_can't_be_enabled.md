---
title: "[SOLVED] visual effects can't be enabled"
date: 2008-01-06
forum: Desktop Effects &amp; Customization
---

### Post by Phil420 on 2008-01-06
it's been a week now that I try to get those enabled, but it ain't working. it says "Desktop effects couldn't be enabled." so i did what someone said, i enabled the restricted driver thing. after that, when i go in Catalyst control center, it says this

[IMG]http://i263.photobucket.com/albums/ii146/420phil/Screenshot-Initializationerror.png[/IMG]

so i installed envy to install the driver but when i reboot my pc, i can't do anything, ubuntu won't work.. it's just a black screen with nothin' happening. i reconfigured the x server and i could go on ubuntu again, exept there's the same box as above... any idea of what to do? i really want that nice cube background.
Thanks!

---

### Post by Phil420 on 2008-01-06
dunno if it could help but my card is Ati X1650 pro

---

### Post by macaholic on 2008-01-06
have you tried isntalling the ATI driver manually? (not the .run file but building .debs and then isntalling them) Also whay is the output of fglrxinfo?

---

### Post by Phil420 on 2008-01-06
> **macaholic said:**
> have you tried isntalling the ATI driver manually? (not the .run file but building .debs and then isntalling them) Also whay is the output of fglrxinfo?

im new to this so i dont get all what ur saying.. but the output is

```

display: :0.0 screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (2.1 Mesa 7.0.1)

```

---

### Post by macaholic on 2008-01-08
sudo apt-get install xserver-xgl should do the trick, and make sure the driver is enabled in System > Administration > Restricted Driver manager, if you want the newer, but more problematic dirver I can point you in the right direction.

---

