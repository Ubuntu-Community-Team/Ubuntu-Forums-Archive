---
title: "Drawer Response in Gnome Panel"
date: 2008-03-11
forum: Desktop Environments
---

### Post by ChaoticVengeance on 2008-03-11
I would like to add one or more drawers to the Gnome panel, but the slow response time it takes for it to open fully keep me from doing so.  Is there any way to remove this lag and have it open immediately after I click on it?

---

### Post by Gen2ly on 2008-03-11
There's a value that can be set in the ~/.gtkrc-2.0 file that lesses the delay of gtk menus to 0.  I'm not sure if this works on drawers.  I have just installed a drawer (but only one) and it doesn't have stuttering so this might do.

```
gtk-menu-popup-delay = 0"| tee -a .gtkrc-2.0
```

P.S. - *This will spit out a warning when starting gtk apps from command line, but it's not a fatal one.*

---

### Post by ChaoticVengeance on 2008-03-11
Newbish question: Where is ~/.gtkrc-2.0?

---

### Post by ChaoticVengeance on 2008-03-12
I think I got this figured out; tell me if I'm wrong.  I create a file named .gtkrc-2.0 in my user directory.  Then I open it and add the line:

gtk-menu-popup-delay=0

save and close it.  I restart X (ctrl-alt-bkspce).  I log in and the delay should be zero.  However, I see no effect on the drawer response time.

---

### Post by Gen2ly on 2008-03-12
yeah that should do it, yes ~ is the user directory.  Thanks for catching my error though.  It appears only "gtk-menu-popup-delay=0" is needed.

---

