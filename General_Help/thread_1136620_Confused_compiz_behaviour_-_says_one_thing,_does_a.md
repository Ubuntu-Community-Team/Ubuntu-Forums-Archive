---
title: "Confused compiz behaviour - says one thing, does another!"
date: 2009-04-25
forum: General Help
---

### Post by anandamide on 2009-04-25
Hey guys n girls n all inbetween;

First off, I've done a (quick) search of the forum and can't find this problem mentioned, although if it's been covered before apologies.

Here's the problem:

1) Go into system -> preferences -> appearance, click any of the compiz-enabled settings

2) PC jitters about a bit, before displaying 'Desktop effects could not be enabled'

3) PC jitters about some more. Screen flickers on and off, new window manager is enabled, pretty compiz effects ensue.

4) Continue as normal, trying to ignore the fact that my computer seems to be pathologically unaware of it's own abilities.

Any ideas what's going on? I'm not terribly fussed, but this issue has remained through two distribution updates and two graphics cards and it niggles me.

For info, here's what the compiz-check script spat out at me:

Distribution:          Ubuntu 9.04
 Desktop environment:   GNOME
 Graphics chip:         nVidia Corporation GeForce 9500 GT (rev a1)
 Driver in use:         nvidia
 Rendering method:      Nvidia

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [ OK ]

Any more info needed just ask :-)

---

### Post by anandamide on 2009-04-25
Bump, anyone?

---

### Post by anandamide on 2009-04-26
OK (and just in case anyone wants to pick this up...), here's the output when running compiz from a terminal:

[FONT="Courier New"]Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Checking screen 1Comparing resolution (1280x1024) to maximum 3D texture size (8192): Passed.
Checking for Software Rasterizer: Not present. 
Checking for nVidia: present. 
Checking for FBConfig: present. 
running under gnome seesion, checking for gnomecompat
Checking for Xgl: not present. 
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format[/FONT]

---

