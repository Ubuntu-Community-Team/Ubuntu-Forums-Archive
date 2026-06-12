---
title: "xubuntu-desktop in edubuntu: xfwm4 not providing title bars, can't drag windows"
date: 2013-06-24
forum: Desktop Environments
---

### Post by UsernameNumber on 2013-06-24
I'm trying to create a modified version of edubuntu that includes the xfce environment from xubuntu (since it's less resource-intensive than Gnome and more nicely configured than the stock Ubuntu xfce4 environment). 

I added the Xubuntu PPA to my Edubuntu machine, and installed xubuntu-desktop, but now xfwm is behaving very strangely. According to ps it is running, and I do get minimize/maximize, etc buttons, resize handles and all that. What I'm missing is the actual title bar of the window-- it's just a semi-transparent block through which you can see the desktop background. If I try to drag a window, the mouse makes a selection box as though the window wasn't there and I was dragging across the desktop. 

I've found reports of similar problems, but nothing quite like this. I tried following instructions that worked for other problems, like running xfwm4 --replace and removing ~/.cache, but no luck. Even tried rebooting, just in case.

Anyone have any idea what might be up?

---

### Post by Toz on 2013-06-24
Do you have an nvidia video card? If so, I recall seeing a bug where if the Window Manager theme has a 1 pixel border, this happens. Try to change the Window Manager theme (Settings Manager -> Window Manager -> Style) and see if another theme works.

EDIT: I think this is the bug report ([https://bugs.freedesktop.org/show_bug.cgi?id=54168]("https://bugs.freedesktop.org/show_bug.cgi?id=54168")).

---

### Post by UsernameNumber on 2013-06-24
Hmm... well, this is interesting. The answer to your question is "yes and no". The server is running in VirtualBox, so it has a virtual video card ("InnoTek Systemberatung GmbH VirtualBox Graphics Adapter"), BUT the underlying hardware is my MacBook, which does have an Nvidia card. 

In any case, your solution worked! It looks like the problem only applies to the Greybird theme and derivatives. Changing to any other theme solves the problem.

Thanks!

---

