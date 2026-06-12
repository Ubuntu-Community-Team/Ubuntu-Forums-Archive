---
title: "LXDE: panel versus dock"
date: 2012-09-24
forum: Desktop Environments
---

### Post by vasa1 on 2012-09-24
I came across [this line]("http://wiki.lxde.org/en/LXPanel"):
> setdocktype=1   # ask the window manager to treat the panel as a dock.
and I came across this thread: [Dock vs Panel; What's the difference?]("http://ubuntuforums.org/showthread.php?t=1732052") in which there seems to be a feeling that there's not much to distinguish one from the other.
But the lxde wiki seems to suggest that some clear difference does exist. Any idea where I could find out more?

---

### Post by black veils on 2012-09-24
dock seems to mean the place in which the window buttons go. so your running applications can show as buttons in the panel, but it is not a required feature, you can have a panel without windows buttons, and just use Alt + Tab (or whatever) to switch between open application windows. you see?

---

### Post by vasa1 on 2012-09-24
> **black veils said:**
> dock seems to mean the place in which the window buttons go. so your running applications can show as buttons in the panel, but it is not a required feature, you can have a panel without windows buttons, and just use Alt + Tab (or whatever) to switch between open application windows. you see?
*dock seems to mean the place in which the window buttons go. so your running applications can show as buttons in the panel,*
In the context of Lubuntu, what you describe is called "Task Bar (Window List)" and it is an *(optional) component* of the panel.
The line that I quoted from the lxde wiki seems to imply that a setting of "setdocktype=1" makes the entire panel acquire a "dock"-like nature as far as the window manager is concerned.
I guess I could try various other values for setdocktype and learn from my own experience but I'd rather find documentation first.

As for alt-tab, that option does indeed allow one to switch between open applications but it's not what is puzzling me.

---

### Post by cwsnyder on 2012-09-24
One of the major differences between a dock and a panel?  A dock is usually configured from the middle out, a panel is usually configured from ends to the middle by default, with pre-configured placement for menu, notifiers, etc.

---

### Post by vasa1 on 2012-09-25
I asked over at the [Lubuntu Mailing List]("https://lists.ubuntu.com/mailman/listinfo/lubuntu-users") and got pointed to a link that answered my question and much more: [http://pclosmag.com/html/Issues/201010/page07.html](http://pclosmag.com/html/Issues/201010/page07.html).
Quoting from there:> 
**Make window managers treat the panel as a dock**: when checked window managers will see the panel as a dock and not a window. It will not be displayed on a list of open windows (e.g. the Alt+Tab window switcher) or the pager. 

---

