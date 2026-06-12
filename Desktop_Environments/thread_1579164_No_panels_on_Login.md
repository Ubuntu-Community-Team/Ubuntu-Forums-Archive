---
title: "No panels on Login"
date: 2010-09-21
forum: Desktop Environments
---

### Post by tnsmart on 2010-09-21
I have a computer which I have just installed Ubuntu on, after wiping the hard drive and everything is fine except that upon login (it is set to login automatically and skip the login screen), no panels appear.  Everything is fully functional: the mouse moves, I can right-click to create a new folder, etc. but I cannot access anything because I have no panels.  I have tried two different monitors, one 17" and one smaller (I think 15") and both do the same thing.  Any ideas how I can correct this?  Thanks.

---

### Post by deesto on 2010-09-21
The normal way to fix this would be to right-click a panel, add a new panel, and add back your menus, launchers, etc., but obviously you can't do that if you don't have any panels ... a new installation should finish up without any visible panels.

Anyway, can you launch a terminal?  If so, is gnome-panel running?  If not, create a new launcher for terminal on your desktop, run terminal from there, and check for gnome-panel (ps auwwx|grep gnome-panel).  If it's not running, try and launch it ... may need to be done as 'sudo' but not likely.  If it starts running, and then if you get a panel from it, you can go from there by adding launchers and menus.

But since the panels are part of the default gnome installation, I would suspect something to be wrong with the install if the normal panels aren't showing up on boot.

---

### Post by Ben_neB on 2010-09-21
Try hitting Alt+F2 and typing in "pkill gnome-panel". That kills your existing panels, but more importantly, it should force them to re-open. If that works, you can just write a script to do that at startup. It's kind of a bandaid solution, but it works.

---

### Post by tnsmart on 2010-09-22
Thanks for the replies.  Strangely, I did try installing Ubuntu multiple times and this happened every time.  Alt+F2 and "pkill gnome-panel" does work.  I would like to reinstall the necessary gnome files but am not sure which packages to select in the Synaptic Package Manager.  Any ideas?  Thanks again.

---

### Post by deesto on 2010-09-22
```
sudo apt-get reinstall gnome-panel
```... should do the trick?  If not, you may have to do a `remove|clean|install` instead of a simple reinstall.

Oh ... and if that fails too, you may have something odd in your personal Gnome configuration files.  You could back up your ~/.gnome2 and ~/.gnome2_private directories (especially ~/.gnome2/panel2.d/), remove them, and try again.

---

### Post by deesto on 2010-10-14
Did you ever get this sorted out?

---

### Post by tnsmart on 2010-10-14
Unfortunately not, nothing worked.
Because I could access any icons on the desktop, I created a launcher that would run the command "pkill gnome-panels" and everything would start working.  The command, or any others, will not run as a startup application on this computer.  Thanks for the help.

---

