---
title: "My LCD brightness keeps getting reset to 50%. Why?!!"
date: 2008-07-26
forum: Desktop Environments
---

### Post by softtower on 2008-07-26
In Gnome, my LCD brightness keeps getting reset to 50% every time I reboot, suspend/resume, power off/on or simply plug/unplug A/C cord.

Note, this has nothing to do with "dim display" option: the option is turned off. Is that a bug or a feature of some sort?

---

### Post by Papi-KB7VGW on 2008-07-26
Hi  I had this problem and here is what I found.  Open a terminal
```
gconf-editor
```

Search for brightness, make sure you check both key names and values.  There are several of them.  I set mine to 100 for ac and 70 for battery.  I also found that something had changed the value in my bios but I don't remember if these were at the same time or not.  I seem to have gotten a bad case of CRS.  Can't remember ....

Hope this helps   Papi

---

