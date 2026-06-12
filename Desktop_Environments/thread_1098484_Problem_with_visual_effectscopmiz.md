---
title: "Problem with visual effects/copmiz"
date: 2009-03-17
forum: Desktop Environments
---

### Post by ravn-hawk on 2009-03-17
Hi guys,

I have a compiz/gnome/ubuntu problem. After a fresh install of ubuntu 8.10 (and also with 8.04) I can turn on visual effect and it's all very nice. However after I change my screen setting for the first time to include the laptop VGA output to use a beamer, then visual effects fail. Compiz saying "Checking for Xgl: not present. " Anyone know how to resolve this?

Complete compiz output:
n$ gnome-appearance-properties 
There is no available graphics driver for your system which supports the composite extension, or the current one already supports it.
Checking for Xgl: not present. 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1400x1050) to maximum 3D texture size (2048): Passed.
Checking for Software Rasterizer: present. 
Software rasterizer detected, abortingaborting and using fallback: /usr/bin/metacity

---

### Post by hangnail on 2009-03-17
do you have intel integrated graphics like the 945GM? then try this:

[http://ubuntuforums.org/showthread.php?p=6797452#post6797452](http://ubuntuforums.org/showthread.php?p=6797452#post6797452)

---

