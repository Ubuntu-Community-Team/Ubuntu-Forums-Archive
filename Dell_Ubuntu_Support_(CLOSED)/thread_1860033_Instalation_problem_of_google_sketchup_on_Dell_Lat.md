---
title: "Instalation problem of google sketchup on Dell Latitude D530"
date: 2011-10-14
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Mac-Atsch on 2011-10-14
Hallo, I have installed google Sketchup thrue the Wine. Installation was correct. But if I want run Sketchup, than its comming this error: 

Sketchup was unable to initialize OpenGL!
Pleas make sure you have installed to correct drivers for your graphics card.
Error: Choose Pixel Format failed

Can somebody help me ?!
I have ubuntu 11.04

Thanks

:popcorn:

---

### Post by fixerdave on 2011-10-15
bug 14045: If you get the error "SketchUp was unable to initialize OpenGL!, run regedit (from the terminal type: wine regedit), open [HKEY_CURRENT_USER\Software\Google\SketchUp8\GLConfig\Display], and change "HW_OK" to 1.
        This is from:  [http://wiki.winehq.org/GoogleSketchup](http://wiki.winehq.org/GoogleSketchup)


Worked for me :)

---

