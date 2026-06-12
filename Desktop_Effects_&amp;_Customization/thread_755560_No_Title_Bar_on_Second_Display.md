---
title: "No Title Bar on Second Display"
date: 2008-04-15
forum: Desktop Effects &amp; Customization
---

### Post by dauclair on 2008-04-15
I am running a dual monitor setup on Ubuntu 7.10. My video card is an ATI Radeon X1600, and I was able to get the proprietary drivers working correctly with dual displays. I also was able to get compiz running and emerald installed, however I can not get the title bar/decorations to show up on the extended monitor. All of the compiz/emerald stuff looks fine on the primary monitor.

I have read posts about similar problems and running session scripts to start emerald on the second display at startup. I have tried: $ emerald --replace --display :0.1
but I always get: (emerald:10264): Gtk-WARNING **: cannot open display: :0.1

I have also tried the command: $ emerald --screen 1
and get:
emerald: Could not acquire decoration manager selection on screen 0 display ":0.0"

Just running: $ emerald --replace only toggles the title bar decorations on the primary monitor.

I feel like this has something to do with the way the ATI proprietary driver names the separate displays, but I'm not sure. It definitely seems like an emerald problem on the second display, since it is only the title bar that doesn't show up but the rest of the windows are normal when dragged to the second display.

Any help would be greatly appreciated. I am fairly new to linux and I love the way compiz looks on my primary monitor, just need it to work with both.

---

### Post by dauclair on 2008-04-15
Also, in case it helps to track things down here is the output when I run $ compiz --replace

```

Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 1002:71c2 (prog-if 00 [VGA])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (2560x1024) to maximum 3D texture size (4096): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting emerald
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format

```

---

