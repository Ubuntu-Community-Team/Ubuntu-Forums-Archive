---
title: "Geometry not sticking on evolution with 8.10"
date: 2009-01-04
forum: Desktop Environments
---

### Post by MalContented on 2009-01-04
Hi,

I have installed ubuntu 8.10 on a new machine and have come across an annoying issue with the geometry of evolution, that is not there on my existing 8.04 installation.

Everything appears to work properly if I log in on the console.  I can start evolution, resize the window, close it down and, when I restart it again, the window opens with the width and height it had when it closed down.  I can do the same from a Cygwin X-server running on a Windows XP box by spawning evolution from an xterm command line.  In this case it always starts up as a very small window and I have to re-size it to make it usable.

I have tried manipulating some stuff in ~/.gconf/apps/evolution/shell/view_defaults/%gconf.xml but whenever I alter anything, gnome sets it back to what it was when evolution exits.  My 8.04 installation (which doesn't have this problem) has a width and height section in this file but 8.10 does not.  Is this an issue with evolution or gnome?  Where is the definitive location for the window geometry?

Versions:
evolution on 8.04 is 2.22.3.1 and on 8.10 is 2.24.2

Any help would be appreciated.

Mal

---

