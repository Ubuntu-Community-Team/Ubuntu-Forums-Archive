---
title: "How do I change desktop right click menu to jgmenu?"
date: 2022-06-03
forum: Desktop Environments
---

### Post by schwim-dandy on 2022-06-03
Hi there!


I did a lot of googling but everything leads to customizing the current right-click menu.
I  would like to change the behavior of right-clicking on the desktop from  the stock xfce menu to opening jgmenu instead.  Is there something I  can edit to change this?


Thanks for your time!

---

### Post by TheFu on 2022-06-03
The right-click stuff is controlled by the Window Manager.  Which WM does xfce use?  Openbox?  Nope, this says [https://docs.xfce.org/xfce/xfwm4/start](https://docs.xfce.org/xfce/xfwm4/start) is the default.  So, I'd start there to seek the options.

[https://github.com/johanmalm/jgmenu/blob/master/INSTALL.md](https://github.com/johanmalm/jgmenu/blob/master/INSTALL.md) spells out the installation requirements. It says something about xfce-panel, but I don't know enough about that to say how integration would happen or what the integration would be.

I think you'll probably find that swapping out the menu isn't possible, but you could setup an accel key-chord to open the menu program/tool you prefer, without the mouse.

---

