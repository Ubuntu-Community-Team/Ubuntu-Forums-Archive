---
title: "Can't enable desktop effects"
date: 2009-09-17
forum: Desktop Environments
---

### Post by rschnitzel721 on 2009-09-17
I have an Asus G50v laptop.  I trying to get my desktop effects to work but I can't enable them.  I have version 180 for my nvidia drivers and compiz downloaded.  If you need system info please include the commands for the terminal I have a horrible memory when it comes to that stuff.

Thanks for the help.

---

### Post by raymondh on 2009-09-17
> **rschnitzel721 said:**
> I have an Asus G50v laptop.  I trying to get my desktop effects to work but I can't enable them.  I have version 180 for my nvidia drivers and compiz downloaded.  If you need system info please include the commands for the terminal I have a horrible memory when it comes to that stuff.

Thanks for the help.

try compiz-check

[http://forlong.blogage.de/entries/pages/Compiz-Check](http://forlong.blogage.de/entries/pages/Compiz-Check)

---

### Post by rschnitzel721 on 2009-09-18
Here is what compiz-check spit back out at me

Gathering information about your system...

 Distribution:          Ubuntu 9.04
 Desktop environment:   GNOME
 Graphics chip:         nVidia Corporation Device 062b (rev a1)
 Driver in use:         nvidia
 Rendering method:      Nvidia

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [FAIL]
 Checking for non power of two support...          [FAIL]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [FAIL]
 Checking for hardware/setup problems...           [SKIP]

At least one check had to be skipped:
 Error: Unable to detect maximum 3D texture size

---

### Post by earthpigg on 2009-09-18
system -> admin -> hardware drivers

are any other drivers available for use (177, etc) and have you tried enabling them?

---

### Post by rschnitzel721 on 2009-09-19
Just installed driver 173 and no help.  I ran compiz-check again and got the same read out as before.

---

