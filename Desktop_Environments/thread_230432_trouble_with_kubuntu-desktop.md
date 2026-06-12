---
title: "trouble with kubuntu-desktop"
date: 2006-08-05
forum: Desktop Environments
---

### Post by ronlybonly on 2006-08-05
I am running Ubuntu 6.06 LTS, and i just grabbed xubuntu-desktop and kubuntu-desktop from the repos. Xubuntu installed without a hitch, but not so with kubuntu :( Every time I try to start KDE or run a KDE-based app, i get a string of error messages:

"There was an error setting up inter-process communications for KDE. The message returned by the system was:

Could not read network connection list.
/home/andy/.DCOPserver_ubuntu__1

Please check that the dcopserver program is running!"

and

"Will not save configuration.
Configuration file '/home/andy/.kde/share/config/kdeglobals' not writable."

I would really appreciate if somebody could give me an "easy fix" to this problem (heck, i would settle for a not-so-easy fix).

---

### Post by the-linux-guy on 2006-08-06
Maybe you should check the file ownership of the users' home dirs.

The home dirs should be owned my their users. Log in as root, right-click .kde in your /home/<username> dir and, under Properties, change the Permissions so that everyone can 'read, write, execute'. Log out as root and log back in as yourself and you should get access to it.

---

### Post by ronlybonly on 2006-08-06
awesome! thanks, everything is working now.

---

