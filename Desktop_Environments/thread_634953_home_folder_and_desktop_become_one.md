---
title: "home folder and desktop become one?"
date: 2007-12-08
forum: Desktop Environments
---

### Post by pienose on 2007-12-08
OK I booted up my computer today to see that all the folders in my home folder have come onto my desktop! and that in the places side-pane my home folder link has gone, when I click on the desktop link it goes to my home folder. So now what it looks like is that my home folder and desktop have merged into one folder, how do I fix this?

P.S: a possible cause could have been that I had the desktop folder in my home folder and that I deleted that, but that was a long time ago.

---

### Post by pienose on 2007-12-09
Cummon people I need at least a temporary fix! :(

---

### Post by puccaso on 2007-12-09
gconf-editor

goto, /apps/nautilus/preferences/desktop_is_home_dir
and see if it is checked, uncheck it - log out and log in again

---

### Post by rune0077 on 2007-12-09
Check this thread: [http://ubuntuforums.org/showthread.php?t=635594](http://ubuntuforums.org/showthread.php?t=635594)

Hope it helps.

---

### Post by realthor on 2007-12-09
Gnome uses a description file for directories like Documents, Desktop, etc.The fix is to go to edit /home/<username>/.config/user-dirs.dirs and change the line XDG_DESKTOP_DIR="$HOME/" to XDG_DESKTOP_DIR="$HOME/Desktop". Log out and back in.

This happened because you probably deleted the Desktop folder in your /home.

---

### Post by gfixler on 2008-02-10
I just wanted to thank realthor - this was exactly the info I've been trying to find, ever since I accidentally moved my Desktop folder, rebooted, realized the mistake, moved it back, and then ended up with a home directory as my desktop after the next reboot.

Thanks!

---

