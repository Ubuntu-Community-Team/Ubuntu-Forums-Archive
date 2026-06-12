---
title: "xorg.conf 0 bytes"
date: 2009-04-27
forum: General Help
---

### Post by cotcot on 2009-04-27
I tried to fix graphics issues (buttons in blender have no icons, slow graphics) on a laptop (Toshiba U400) with GM45 chipset following [[COLOR="Red"]this[/COLOR]]("http://www.ubuntugeek.com/intel-graphics-performance-guide-for-ubuntu-904-jaunty-users.html") guide.
Everything went fine until the editing the xorg.conf to enable UXA. There is a /etc/X11/xorg.conf and even a second xorg.conf with the date in the filename when I did the upgrade from intrepid to jaunty (25/4).
Both xorg.conf files are empty. Where can I find them ?

---

### Post by antikristian on 2009-04-27
Newer xorg versions do not really need a xorg.conf, most of it is done trough udev automatically. You can still add options in xorg.conf though, and it's possible to use a conventional xorg.conf.

If you need to add an option, it's also possible to edit udev rules to enable these options, don't as me how though, it's been a while since I edited one.

Try to just add the option under the correct section in xrg.conf. If xorg.conf is completely empty, you can generate a new one with ```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by cotcot on 2009-04-28
Thanks.
I enabled uxa in xorg.conf. The graphics of the GM45 chip is better now. Unfortunately the buttons in blender still have no icons.

---

### Post by cotcot on 2009-05-02
Got all problems solved with EXA in xorg.conf and the latest xserver-xorg-video-intel (2.2.7)

---

