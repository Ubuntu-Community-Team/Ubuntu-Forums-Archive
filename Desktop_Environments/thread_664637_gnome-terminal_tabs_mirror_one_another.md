---
title: "gnome-terminal tabs mirror one another"
date: 2008-01-11
forum: Desktop Environments
---

### Post by kbrede on 2008-01-11
I found one other person with this problem in the archives.
[http://ubuntuforums.org/showthread.php?t=299240](http://ubuntuforums.org/showthread.php?t=299240)

Basically whatever I do in one tab is mirrored in all the other tabs.  If I ssh to a server then all the tabs are logged into the same server.  I tried purging the gnome-terminal package and reinstalling but that didn't help.  This is a fresh install of 7.10 desktop.  Gnome-terminal version 2.1.2.  Anyone know how to fix this problem?
Thanks,
Kent

---

### Post by kbrede on 2008-01-11
I ended up removing the gnome dot files from my home directory and restarted the gnome session.  That seems to have fixed the problem.  
Kent

---

