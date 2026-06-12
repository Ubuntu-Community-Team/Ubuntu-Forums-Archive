---
title: "Lost all control of windows"
date: 2011-08-21
forum: Desktop Environments
---

### Post by dcroxton on 2011-08-21
This is a very strange problem that just started today.  Suddenly, my windows have no borders, and I have little control of them -- no moving, minimizing, or maximizing.  I can't access these functions because there is no bar at the top, but they also don't respond to pressing the Alt key.  My mouse cursor is the generic "X" that XWindows starts with.

The obvious solution is to change my settings, but I can't:  when I try to open window manager settings, the disk spins a little but nothing shows up.

Another solution would be to try a different window manager, but this fails on a different problem that I have been having for some time.  If I log out and then click on my user name to log back in, nothing happens -- I do not get a password box, just the same user selector that I started with.  I use Xfce and I don't know how to switch.

Any help would be greatly appreciated.

---

### Post by dcroxton on 2011-08-21
Well, heck, I just found the solution here:  [http://ubuntuforums.org/showthread.php?t=1425312&highlight=Lost+control+windows](http://ubuntuforums.org/showthread.php?t=1425312&highlight=Lost+control+windows).  The window manager was not running, so I had to run an xfwm4 command.  I'm not going to mark this as solved until I establish that it will work when I restart -- if not, I need to know how to get the window manager to start automatically.

---

