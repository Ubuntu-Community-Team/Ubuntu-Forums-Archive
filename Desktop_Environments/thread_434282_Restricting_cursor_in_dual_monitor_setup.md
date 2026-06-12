---
title: "Restricting cursor in dual monitor setup"
date: 2007-05-05
forum: Desktop Environments
---

### Post by FooSoft on 2007-05-05
Is there an easy way to keep the mouse cursor from being able to cross between monitors in a dual monitor setup? My second monitor is actually an HDTV that I use for movie out, but it sucks that I can lose my cursor in there when it's off.

Ideally there would be some tool/setting that would allow me to:
1) Constrict cursor to the current display
2) "Teleport" the cursor between the two monitors.

Any ideas? I know this is kind of weird but hopefully something like this exists.

---

### Post by FooSoft on 2007-05-06
No ideas heh? Is this something I'd just have to write myself?

---

### Post by airtonix on 2007-09-26
First i found this : 
> 
~$ sudo apt-cache search display | grep between
dirdiff - Display and merge changes between two directory trees.
kompare - a KDE GUI for viewing differences between files
teleport - moves running applications between displays
xmove - allows you to move programs between X Window System displays


Then, installed teleport and ran it. It tells me there are no apps that support the "display migration protocol".

Googling for "display migration protocol" reveals : [http://lists.freedesktop.org/archives/xdg/2004-November/003854.html](http://lists.freedesktop.org/archives/xdg/2004-November/003854.html)

which goes onto mention : 
> 
If the client who owns the window wants to allow moving it to a
different display, it puts the _NET_CHANGE_DISPLAY atom in the
WM_PROTOCOLS property on window.


So the question remains, do we have to recompile our apps to include this property in its window class?

Or can we use some file (~/.teleport-supported-gtk-programs-list) that provides a overlay patch 

Or do we wait for next release of Ubuntu....one that has all its gnome-apps including this "_NET_CHANGE_DISPLAY" property?

---

