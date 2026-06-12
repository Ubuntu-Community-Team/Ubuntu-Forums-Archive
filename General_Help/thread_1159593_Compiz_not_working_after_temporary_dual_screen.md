---
title: "Compiz not working after temporary dual screen"
date: 2009-05-14
forum: General Help
---

### Post by shortylonglegs on 2009-05-14
Playing around with my laptop, I tried to attach it to a spare screen I had.  I didn't like the resolution and general setup of dual screen, and since I didn't really care I just went back to using the laptop's built in screen.  The problem now is that compiz isn't working at all.  After reading some of the other posts, I ran the compiz check script:

```

$ ./compiz-check 

Gathering information about your system...

 Distribution:          Ubuntu 9.04
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

```

Also:

```

$ compiz
Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Checking screen 1Comparing resolution (1280x800) to maximum 3D texture size (2048): Passed.
Checking for Software Rasterizer: present. 
Software rasterizer detected, abortingaborting and using fallback: /usr/bin/metacity 

```


I don't really know what that means or what a software rasterizer is.  Does anyone know how to fix this?  I did try restarting, and reinstalling compiz, but none of that helped.  Compiz worked without a problem before I tried dual screen, and stopped working immediately after.

---

### Post by Scott Deagan on 2009-07-22
I too have had problems with dual-screen/Compiz Fusion. If returning to a single screen, you can delete your /etc/X11/xorg.conf file, then restart Ubuntu:

1. Start terminal.
2. sudo rm /etc/X11/xorg.conf
3. sudo reboot

(probably better to back it up first: 
[FONT=Courier New]sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak[/FONT])

I really hope Ubuntu makes switching between single/dual screens much easier in the future, and that Compiz Fusion will work seemlessly when switching between the two. At the moment it's very confusing and seems to be comparable to a lucky dip (works for some graphics cards, not so well for others).

---

### Post by Nycthbris on 2009-07-30
Thanks for the info. Fixed the same problem for me after fiddling with an external monitor via the DVI out on my Macbook.

> **Scott Deagan said:**
> I too have had problems with dual-screen/Compiz Fusion. If returning to a single screen, you can delete your /etc/X11/xorg.conf file, then restart Ubuntu:

1. Start terminal.
2. sudo rm /etc/X11/xorg.conf
3. sudo reboot

(probably better to back it up first: 
[FONT=Courier New]sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak[/FONT])


DEFINITELY backup your xorg.conf, its an important file :)

---

