---
title: "Screen Resolution Issue on Vostro 1500"
date: 2008-02-13
forum: Dell  Ubuntu Support
---

### Post by charco83 on 2008-02-13
Last night after installing Ubuntu 7.10 I decided to try out my laptop with my external monitor.  One way or another I've mucked up the monitor resolution settings so that the laptop display is now all lines.  Obviously this makes it very difficult for me to go back into the settings and reset them.

Is there an easy way to set the resolution to something that would allow me access (a safe mode?).

---

### Post by jan quark on 2008-02-14
what are your specs?
grpahics?



you can try to boot into the safemode

during the booting process the grub loader should give you some seconds to enter the grub menu

there select safemode and you should enter the console

now run this command
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
try now to boot into the normal mode

---

