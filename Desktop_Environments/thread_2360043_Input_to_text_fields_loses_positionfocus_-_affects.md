---
title: "Input to text fields loses position/focus - affects multiple apps"
date: 2017-05-01
forum: Desktop Environments
---

### Post by aylwyn on 2017-05-01
I have an annoying UI bug in 16.04 which affects several programs and thus is possibly Gnome/GTK related.

Specifically, on input into a text entry field (e.g. in a dialog box, toolbar or palette), the first character inputted (including delete) is accepted, but the second is ignored/erased and instead the input position jumps to the start of the field. I have to manually reposition the input I-bar each time using the mouse or arrow keys.

So far I've found this to affect most or all text entry fields in Nautilus, Inkscape, and GIMP; but not LibreOffice or Chrome. 

It's a relatively new & clean install of 16.04 on a Dell XPS 13. I did configure sloppy focus with the Unity Tweak tool, but other than that haven't done anything particularly funky.

Anyone got any ideas what this might be? Seems possibly similar to a couple of reported bugs e.g. [https://bugs.launchpad.net/ubuntu/+source/ibus/+bug/1385292](https://bugs.launchpad.net/ubuntu/+source/ibus/+bug/1385292).

---

### Post by aylwyn on 2017-05-04
Not that anyone seems interested :) but I appear to have fixed this by reinstalling ubuntu-desktop and resetting Unity back to default settings.

---

