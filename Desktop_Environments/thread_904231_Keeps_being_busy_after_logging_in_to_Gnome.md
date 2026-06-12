---
title: "Keeps being busy after logging in to Gnome"
date: 2008-08-29
forum: Desktop Environments
---

### Post by Tomatosoup on 2008-08-29
Hello,

I've got a bit of an annoyance. When I log in to Gnome the mouse cursor changes into the 'busy mouse cursor'. And it never becomes a normal one (well, at least not on the desktop itself but with other applications it does change to a normal cursor though). I've looked at the Process Manager, and it doesn't show a high CPU load by any of the processes, accept a bit CPU load for the Process Manager itself.

What could this be, and how can I solve this?

---

### Post by Jamin3D on 2008-09-16
I've got this exact same problem.  If you come up with anything, please post!

---

### Post by Jamin3D on 2008-09-16
Got it fixed!  Check NiceGuy's post here:

[http://ubuntuforums.org/showthread.php?p=4414151#post4414151](http://ubuntuforums.org/showthread.php?p=4414151#post4414151)

I also had a bad "x-nautilus-desktop..." entry.  Removed it, saved the .gtk-bookmarks file, logged off & back on, and problem fixed!  No more needless busy cursor.  :)

---

