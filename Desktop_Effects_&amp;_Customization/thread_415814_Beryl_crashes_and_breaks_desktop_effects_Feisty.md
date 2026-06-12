---
title: "Beryl crashes and breaks desktop effects Feisty"
date: 2007-04-20
forum: Desktop Effects &amp; Customization
---

### Post by dgel on 2007-04-20
Hi 

I just installed Feisty and wanted Beryl, so I installed all the necessary packages.
Now when i launch it, the screen flickers and then returns to normal. When i select beryl as window manager a lot happens for a second and it crashes back to metacity. 
Also after installing it, the desktop effects (wobbly windows and the cube) no longer work.
The error message simply states "Desktop effects could not be enabled"

I'd like to know if there is a way to get it working or at least to get it back to the previous state w/out a fresh install.

I'm sorry if this is just another Beryl + Feisty message, but I honestly couldnt find this particular error in the forum.

Na-FIann

---

### Post by jaimz on 2007-04-20
what gpu are you using?

---

### Post by dgel on 2007-04-21
I use the Radeon 9600 pro, with the the restricted drivers from the feisty manager

---

### Post by jolsz on 2007-04-21
> **Na-Fiann said:**
> I use the Radeon 9600 pro, with the the restricted drivers from the feisty manager

I use the same card with ati driver:

Section "Device"
        Identifier      "ATI Technologies Inc RV350 AP [Radeon 9600]"
        Driver          "ati"
        BusID           "PCI:1:0:0"
        Option          "UseFBDev"              "true"
        Option          "XAANoOffscreenPixmaps" "true" 
EndSection

Just changing the driver will solve your problem.

---

### Post by dgel on 2007-04-21
Thanks for the tip, but I'm not that linux savvy... could you explain how to do this? as i said, i just used the gui that came with feisty :P

---

### Post by cwelch on 2007-09-02
I have the same problem, but I use a 915* Intel in my laptop. If you get any ideas or solutions, send them my way pleasse!

---

### Post by Inxsible on 2007-09-02
> **jolsz said:**
> I use the same card with ati driver:

Section "Device"
        Identifier      "ATI Technologies Inc RV350 AP [Radeon 9600]"
        Driver          "ati"
        BusID           "PCI:1:0:0"
        Option          "UseFBDev"              "true"
        Option          "XAANoOffscreenPixmaps" "true" 
EndSection

Just changing the driver will solve your problem.

> **Na-Fiann said:**
> Thanks for the tip, but I'm not that linux savvy... could you explain how to do this? as i said, i just used the gui that came with feisty :P
You need to look at the Device Section in your xorg.conf file.

you can open your xorg.conf file like so. In a terminal type in```
gksudo gedit /etc/X11/xorg.conf
```

---

