---
title: "xubuntu 7.10 desktop problem"
date: 2007-10-21
forum: Desktop Environments
---

### Post by cronohl on 2007-10-21
im using the live disk and when every thing loads up the tool bars on top and bottom are not there 

and the cd does not have any errors and i have tryed messing with the monitor L&W

---

### Post by gp95ac on 2007-10-22
how did you mess with the monitor L&W, buttons on the front, or with 
sudo dpkg-reconfigure -phigh xserver-xorg

hit alt +f2, paste the above and run it in a terminal, youll get the resolution options you need,
it may be that the buttons cannot shrink it down enough to see the panels

---

### Post by cronohl on 2007-10-22
i cant get to the buttons from right clikc

it dont matter if its 800x800 or 1000x 1200 

just cant see em

---

### Post by cronohl on 2007-10-22
bump

---

### Post by gp95ac on 2007-10-23
What buttons? Havent used xfce in a while...are we talking "add panel"?  They should be there by default.

Maybe try re dl-ing and reinstalling Xubuntu, or a different flavour (ubun or kbun)?  That is, if you are not bound by system capabilities.  Along those lines, how about a different WM, fluxbox is just as fast, if not faster on older systems.

---

### Post by gp95ac on 2007-10-23
How about some system specs? Might help point you to the proper distro

---

### Post by vambo on 2007-10-23
> **cronohl said:**
> im using the live disk and when every thing loads up the tool bars on top and bottom are not there 

and the cd does not have any errors and i have tryed messing with the monitor L&W

Xubuntu aka XFCE, doesn't have gnome style  top and bottom panels. On a fresh desktop you'll just have some desktop icons and a bare XFCE panel. To get the menus, right mouse button.

---

### Post by gp95ac on 2007-10-23
Not true (the no panel comment), at least not with my live CD.  It had been a while, so I took it for a spin.

---

### Post by gp95ac on 2007-10-23
both top and bottom are there

---

### Post by santiagoward2000 on 2007-10-23
Perhaps they're just not loaded. Try pressing Alt+F2 and then type:
```
xfce4-panel
```

---

