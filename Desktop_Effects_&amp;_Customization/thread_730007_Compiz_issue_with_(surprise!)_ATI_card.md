---
title: "Compiz issue with (surprise!) ATI card"
date: 2008-03-20
forum: Desktop Effects &amp; Customization
---

### Post by kazuo71 on 2008-03-20
Right, I've been trying to get Compiz working with my ATI Radeon HD 2400 Pro AGP for a while now. I get the usual "Desktop effects could not be enabled" when i try to enable the effects. The dirvers for my graphics card were installed using Envy and went very smooth, resolution is good etc., but I can't get the infamous Compiz working with my card :(. Using Ubuntu Gutsy 7.10 btw.


Here's what i get when i type 'compiz' in terminal:

Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 1002:94c4 (prog-if 00 [VGA])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1680x1050) to maximum 3D texture size (8192): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz: 378: /usr/local/bin/compiz: not found

I'm hoping I've done some usual noob mistake that can be easily corrected.
If you need anymore information, please speak out (xorg.conf possibly?)!


Hoping someone can help me out, would be very grateful :popcorn:

---

### Post by erdnuss on 2008-03-20
Hey kazuo71,


try this

vi /usr/bin/compiz

edit this line (line 31


from
PLUGIN_PATH="/usr/local/lib/compiz/"

to
PLUGIN_PATH="/usr/lib/compiz/"

it should now find your plugins.


ref: [http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide)
section 3Ddesktop effects


cheers!

---

