---
title: "Losing Window Focus and Key Bindings in GNOME!"
date: 2007-02-13
forum: Desktop Environments
---

### Post by grnwood on 2007-02-13
Okay I've been banging my head against the boards on this one.

I have an issue whereby in GNOME I lose the ability to focus a window by clicking on the window contents.  I instead have to click on the titlebar of the window to get focus.  At the same time, I lose all my custom keybindings and even the ability to ALT-TAB to change windows.  The only way to fix this issue is to restart X.  

I was trying to isolate this problem to either the window manager (metacity)  or the desktop environment (gdm/GNOME).  In doing so I replaced metacity with xfwm via: 

[http://ubuntuforums.org/archive/index.php/t-88393.html](http://ubuntuforums.org/archive/index.php/t-88393.html)

And for some time thought the problem was fixed.  However, the exact same symptoms came back with a totally different window manager.

I have tried manipulating all the focus settings of both metacity and xfwm to no avail, as well as deleted all my .gnome, .gnome2, .gonf*, and .metacity directories.  None of this has worked.  I've also been searching on the GNOME boards and not finding anything.  This definately appears to be a GTK+/GNOME issue, has anyone had any similar experiences?

Thanks

---

### Post by ggeldenhuys on 2007-05-03
This has been driving me nuts as well. I have had this issue on two PC's since I installed Ubuntu 7.04.  I never experienced this before on other Ubuntu versions.

For now, my work-around is to set the Focus and Bring To Front on mouse hover. Though that is very annoying.

It seems more and more people are experiencing this problem, but I haven't found any fix for it yet.  If this keeps up, I might just go back to Ubuntu 6.10.

---

