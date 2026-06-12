---
title: "VGA mode not support on boot"
date: 2010-05-26
forum: Dell Ubuntu Support (CLOSED)
---

### Post by qwiktune on 2010-05-26
I just fresh installed Ubuntu Lucid along side my windows xp, had to use the Alternate CD instead of Live CD cuz i was gettin this error, but now its all installed and when I go to load it up after Grub the screen goes black and my monitor is saying VGA mode not support, how do I fix this so I can fire up Ubuntu? I have it on a Dell Dimension 2400 with whatever integrated card using the suggested driver from Dells website for this model computer 

this might help?

00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)

---

### Post by 2hot6ft2 on 2010-05-27
Give this a shot
Open a terminal
Applications > Accessories > Terminal
and run
```
gksu gedit /etc/default/grub
```
change this
> #GRUB_GFXMODE=640x480
to this
> GRUB_GFXMODE=800x600
You could also leave it at 640x480 but most people want more resolution, it's up to you, but remove the # sign at the beginning of the line.
Save and Close then run
```
sudo update-grub
```
reboot
You can undo it if it doesn't help. Just be sure to run update-grub after making changes.
:guitar:

---

