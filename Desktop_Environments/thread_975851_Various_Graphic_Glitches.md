---
title: "Various Graphic Glitches"
date: 2008-11-08
forum: Desktop Environments
---

### Post by metaloph1l on 2008-11-08
Dear Kubuntu Users,
Today I installed Kubuntu on the laptop of my girlfriend. Her specs:
[LIST]
[*]Acer Extensa 5620Z
[*]Intel Pentium Dual Core T2370 (1.73Ghz)
[*]Mobile Intel Graphics Media Accelerator X3100 (965GM/GL960)
[*]2GB DDR2 Ram
[/LIST]

Installation (64-bit) was very smooth including the installation of wifi (wpa2 personal). However, I got various graphic glitches and today I installed Firefox 3.0.3 and its got even more glitches. The attachment shows some of the display bugs:
Some bugs occur on the tab bar, some occur in the page itself, e.g. at the bottom of the tab bar are some artifacts (looks like top of tabs?). Also if i hover over a tab and move the mouse away from the tab (w/o selecting it) it doesn't gray out, the graphics stay in "hovering" mode until firefox is refreshed. In Google checkboxes are placed in obscure gray rectangles, same goes for the textbar itself. I highlighted the bugs in the picture.

Also there are other glitches, e.g. when I minimize (and/or reopen) a program from the taskbar (or resize e.g. adept) the content of the program is warped(distorted) but gets normal again when its minimized or when its fully open.


Now my question: Does it have to do with the graphics adapter X3100 or does the problem have to do with the 64-bit installation (and incompability with Firefox) or is it whole different problem?  These bugs don't occur in Konqueror, however we really want to use Firefox its exstensions. What would you recommend?

Thanks in advance to anyone trying to help me. If i posted this in the wrong section, please move it to the right one. If you need more information please ask. 

Other than that my girlfriend and I are very satisfied with Intrepid Ibex. :KS

Thank you
metaloph1l

---

### Post by jack_spratt on 2008-11-10
I have exactly the same problems as depicted in your secreenshot (kubuntu 8.10 64bit KDE4).

Anyone know how to fix them, or if a replacement package is underway?

These problems don't affect functionality, they just look terrible.

---

### Post by kde4-core-user on 2008-11-10
This is a gtk-qt-engine Issue and can`t be resolved by now. I hope a later version makes it better.

I use gtk2-engine-qtcurve in KDE 4.1.3, which looks pretty good.

This style here seems also to be a good alternative (Package gtk2-engines-qtpixmap is additionally necessary):
[http://kims-area.com/?q=node/63](http://kims-area.com/?q=node/63)

---

