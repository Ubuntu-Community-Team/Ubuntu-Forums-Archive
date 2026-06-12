---
title: "Some tertiary keys (with Alt Gr) work incorrectly"
date: 2010-10-17
forum: Desktop Environments
---

### Post by bitpicker on 2010-10-17
Yesterday I set up a new computer with Ubuntu 10.10 64 bit. My keyboard layout is German and I also added Russian because I use that language as well. 

I found that the German layout types some incorrect symbols in conjunction with Alt Gr. Alt Gr + 8 should give me an opening square bracket, but instead gives me a bullet; Alt Gr + 7 gives me an ampersand, but should give me a wavy opening bracket. The closing brackets on Alt Gr + 9 and 0 respectively are OK. I've also lost the tilde symbol, I get yet another closing square bracket in its place. The backslash on Alt Gr + ß key isn't working either. This is highly annoying...

This is true for all fonts and different keyboard models. I have a Cherry CyMotion Master Linux and set it accordingly. I have also made sure that the third keyboard level is accessed using the Alt Gr key, which for whatever reason is listed as ISO_L... instead of Alt_Gr in the overview, which I have made a screenshot of which is here: 

[http://www.nyboria.de/screenshots/Arbeitsflaeche_1_003.png](http://www.nyboria.de/screenshots/Arbeitsflaeche_1_003.png)

Most keys at the third level are OK, but not all. Strange enough, everything is correct in the same version if booted from the CD, it's just the installed version which shows this problem.

---

### Post by bitpicker on 2010-10-25
Further info: I booted the system from the CD and on that one the layout is correct. I even copied over the information in /usr/share/X11/xkb from the CD to the installed system, but that did not change anything.

I reinstalled the system, and during the installation I checked the layout in the text field supplied for that, and it worked correctly. But the freshly installed system then had the same erroneous layout.

Using the xmodmap command to remap the symbols, I cannot change the third level of the 8 key:

sudo xmodmap -e "keycode 17 = 8 parenleft bracketleft"

All this does is remove the bullet, but it does not show a left bracket; Alt Gr + 8 simply does not produce any symbol then. But if I swap parenleft and bracketleft in the command, then Shift + 8 will give me the left bracket, while Alt Gr + 8 remains without function.

---

