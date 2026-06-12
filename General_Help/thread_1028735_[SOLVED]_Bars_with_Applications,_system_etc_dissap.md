---
title: "[SOLVED] Bars with Applications, system etc dissappeared"
date: 2009-01-02
forum: General Help
---

### Post by tonymhs2009 on 2009-01-02
The bars at the top and bottom of my screen have totally disappeared. Any ideas? (I am using Xubuntu 8.10) Sorry I don't really know what those bars are called but they are the gray one's at the top and bottom of the screen. I'd appreciate it if anyone can help because i am a noob in the world of Linux. 

Thanks

EDIT: Please let me know if I need to be more descriptive.

EDIT: Panels have disappeared.

---

### Post by tonymhs2009 on 2009-01-03
Bump

---

### Post by plucky on 2009-01-03
> **tonymhs2009 said:**
> The bars at the top and bottom of my screen have totally disappeared. Any ideas? (I am using Xubuntu 8.10) Sorry I don't really know what those bars are called but they are the gray one's at the top and bottom of the screen. I'd appreciate it if anyone can help because i am a noob in the world of Linux. 

Thanks

EDIT: Please let me know if I need to be more descriptive.

They are called the panels.

Right click on the desktop and start a terminal window and type in ```
xfce4-panel &
exit
```
and see if that brings back the panels.Do not close the terminal window using the X in the top right hand corner.

Good Luck

---

### Post by tonymhs2009 on 2009-01-03
Without my panels, how can I open terminal?

---

### Post by tonymhs2009 on 2009-01-03
Bump

---

### Post by plucky on 2009-01-03
Sorry I have Xubuntu set up to show the menu on right click.


1) Right click > Desktop Settings > Behavior > Tick Show Desktop Menu on Right Click 

or 

2) Create launcher and use command xfce4-terminal to create a terminal launcher.Then do the previous commands.


Good Luck

---

### Post by tonymhs2009 on 2009-01-03
Awesome. That worked perfectly I really appreciate it.

---

