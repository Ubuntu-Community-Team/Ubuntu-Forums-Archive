---
title: "Desktop Navigation disapears"
date: 2009-08-16
forum: Desktop Environments
---

### Post by AmerNewbieInDE on 2009-08-16
I have a problem, and i hope i explain it good enough.

I am running compiz also screenlets. My screenlet keeps disapearing on me, but thats not the main problem, 

If i click on one of the desktops, on the lower right of the screen, all navigation is gone. Meaning, no taskbar, menubar. I am only left with my desktop wallpaper, nothing to click to get back. It is not frozen though, i can still use the mouse to move my cube, but every screen is the same, also key board works.

I have an acer aspire 8730, ubuntu 9.04 w/kernel 2.6.31, intel core 2 duo @ 2.00GHz, 4G sdram and nvidia 9600M..

HELPPPPP please..

---

### Post by mcduck on 2009-08-16
Check your desktop size settings in CompizConfig Settings Manager (under General Options/Desktop Size), and make sure that "Number of Desktops" is set to one.

The amount of virtual desktops is controlled with horizontal & vertical virtual sizes, not the number of desktops. For normal cube setup you'd have horizontal size of 4, and both vertical size & number of desktops set to 1. If you now set the number of desktops to 2 you'll get two cubes, each with 4 virtual desktops, but the default setup only runs the panels on the first desktop so the second one would be just an empty cube.

---

### Post by AmerNewbieInDE on 2009-08-16
thankyou..... that was it

---

### Post by AmerNewbieInDE on 2009-08-16
ok, well, is there away to get rid of those desktops.. if i dont really need them?? 

also, when i am in the cube, i only see the lower half, the rest is off screen and vertical size is set to 1

---

