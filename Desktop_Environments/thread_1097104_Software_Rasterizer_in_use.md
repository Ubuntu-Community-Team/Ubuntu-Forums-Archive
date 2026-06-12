---
title: "Software Rasterizer in use"
date: 2009-03-15
forum: Desktop Environments
---

### Post by woknam66 on 2009-03-15
I have a Dell Inspiron 6000. I had an external 5:4 monitor attached to my laptop as a "clone", and it worked fine. My desktop effects used to to work on "Extra" and I used a bunch of stuff with Compiz. Then I tried using my external monitor as an extended desktop, and that failed miserably. I then switched it back to a clone, but I wouldn't switch back to being a 5:4 clone, it would only be a 4:3 clone. Also, my desktop effects went back to "none", and whenever I try to raise them even to "normal", it says "Desktop effects could not be enabled." I did [this]("http://forlong.blogage.de/entries/pages/Compiz-Check"), and here is the output:```
Gathering information about your system...

 Distribution:          Ubuntu 8.10
 Desktop environment:   GNOME
 Graphics chip:         Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
 Driver in use:         intel
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [FAIL]

There has been (at least) one error detected with your setup:
 Error: Software Rasterizer in use 

```What should I do?

---

### Post by Forlong on 2009-03-16
Please post the content of your **/etc/X11/xorg.conf**

---

### Post by woknam66 on 2009-03-17
Nevermind, I restarted the computer and booted into recovery mode, did everything there, and now it works fine.

Is there any way that I can delete my own thread?

---

