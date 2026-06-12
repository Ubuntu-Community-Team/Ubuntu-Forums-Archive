---
title: "Starting gnome breaks my monitor"
date: 2005-08-11
forum: Desktop Environments
---

### Post by tazolvear on 2005-08-11
So when I go to start gnome, my monitor switches off for a minute, and then comes back displaying "Invalid Scan Freq." along with some garbled scrolling color effects.

I just installed Ubuntu today, I don't remember being given any video related options that I could mess up during the install except for the choice of screen resolutions, but I just left that at the default selection of 640x480, 800x600 and 1024x768.

I'm using a cheap little PCI video card and the monitor is an older 21" mode, supports up to 1856x1392 on my windows machine.

I'm pretty new, so I don't even know where to start trying to fix this.  Any help is appreciated.

---

### Post by blind0wl on 2005-08-11
When you get the error, Ctrl+Alt F1 to get to a console screen, login and try:

```
sudo dpkg-reconfigure xserver-xorg
```

This wil resetup your Xserver display....

---

### Post by heimo on 2005-08-11
I would try to reconfigure Xorg. For instructions:
[http://www.ubuntuforums.org/showpost.php?p=129379&postcount=21]("http://www.ubuntuforums.org/showpost.php?p=129379&postcount=21")

EDIT: blind0wl  seems to agree ;)

---

### Post by tazolvear on 2005-08-11
Hey, that worked.  Thanks a lot!

---

