---
title: "sorting out desktops in compiz"
date: 2009-01-28
forum: Desktop Environments
---

### Post by ray field on 2009-01-28
finally getting a little bit comfortable with compiz, but still a bit confused about desktops -- I've got the cube spinning horizontally with, I guess, two side-by-side desktops, and using the fixed window settings, have set individual apps to open in separate windows.



however, since sometime after installing cairo-dock a week or two ago, I haven't been able to create/use a desktop underneath the first one.  that is, if there are four possible desktops



1 2

3 4



right now I can only go between 1 and 2, and don't know how to create 3 and rotate the cube vertically so to speak.



likewise, before installing Cairo-Dock and compiz, Ctrl-Alt and any of the arrow keys could switch my desktops easily.  after tweaking the impressive-but-confusing array of options in compiz, though, only Ctrl-Alt-Left and Ctrl-Alt-Right spin the desktop cube...


also, is there a way to set different backgrounds for different desktops (so I can instantly tell which one I'm on if there aren't any windows open?)

tia

---

### Post by gettinoriginal on 2009-01-28
The top and bottom of the cube are not meant to be workspaces, they are cube caps.  You can create 4 workspaces, but that just makes it a 4 sided cube instead of 2.  :p  And yes, you can change the wallpapers:
alt-F2, type in gconf-editor-->hit run

Go under apps > nautilus > preference

Deselect ‘Show Desktop'  Then go to CCSM and enable Wallpaper under Utility, click it and insert the pics or wallpapers you want  :p

Caution, disabling desktop will take icons off the desktop, so you will have to go to "places" "desktop" to see your icons.

---

### Post by ray field on 2009-01-28
thanks.  I guess that means, if a window is sized so that the bottom extends below the desktop, I can't use the cube to get access to it. (I'm using -- and very much enjoying -- Intrepid on an eeePC, and sometimes this happens.)

---

### Post by gettinoriginal on 2009-01-28
Try this to correct window size.  Manually minimize window (even if it is already minimized, minimize it more), close window, then open it and maximize it with the max button in upper right corner.  If that does not work, are you sure your resolution is set right??  And by the way, welcome to Ubuntu :popcorn:

---

### Post by Therion on 2009-01-28
> **ray field said:**
> ... I guess that means, if a window is sized so that the bottom extends below the desktop, I can't use the cube to get access to it. 
Think of the Cube as four, *horizontal*, desktops attached by their vertical edges.  

You can't access the "top" and "bottom" panes of the cube, you can only rotate it on the horizontal axis.  

It's a cube, but with *four* accessible desktops, not six.

---

### Post by ray field on 2009-01-28
> **gettinoriginal said:**
> Try this to correct window size.  Manually minimize window (even if it is already minimized, minimize it more), close window, then open it and maximize it with the max button in upper right corner.  If that does not work, are you sure your resolution is set right??  And by the way, welcome to Ubuntu :popcorn:

I've have tried all kinds of dragging and minimizing with no luck.  it's actually a minor annoyance, and though the better solution is to view the app from the desktop below, after a few weeks now, I'm capable of sussing out which key to press with Alt to close/the resolution is set as fine as I can make it -- looks quite handsome, in fact.

thank you kindly.  still using my beloved old OS/2 setup on my main 'pute, but after somewhat abortive attempts at Suse (9.2 & 10.2), Ubuntu looks quite nice, and I'm very relieved that if/when the OS/2 box gives up the ghost, I'll be ready.

---

