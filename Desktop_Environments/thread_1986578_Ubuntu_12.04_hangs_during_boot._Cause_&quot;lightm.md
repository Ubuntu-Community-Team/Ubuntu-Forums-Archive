---
title: "Ubuntu 12.04 hangs during boot. Cause: &quot;lightm  1.2.1&quot;"
date: 2012-05-25
forum: Desktop Environments
---

### Post by miroi on 2012-05-25
Hi all, 

just to share my experience after few days of struggling.

I have AMD64 QuadCode, Ubuntu 12.04, nvidia GF9800 with "nvidia-current" graphics driver (pointed to by /etc/X11/xorg.conf, which is generated through "sudo nvidia-xconfig"). I made fresh update of yesterday.

It happens that during boot (with text output enabled in /etc/default/grub) my computer hangs on "* Checking battery state" or other text booting message.

However, through CTRL+ALT+F1 I was able to log in, so I was trying to to start X screens. Commands lightm, startx failed (startx giving "No protocol specified"); purging and re-installation of Xserver & nvidia related packaged didn't help.

Finally I replaced the default "lightdm" 1.2.1 manager with the "gdm" and I am able to log in in the graphics mode again.

---

