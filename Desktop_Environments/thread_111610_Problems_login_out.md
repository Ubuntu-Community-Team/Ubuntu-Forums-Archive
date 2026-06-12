---
title: "Problems login out"
date: 2006-01-02
forum: Desktop Environments
---

### Post by labrie on 2006-01-02
Maybe this is  the  most stupid problem  ever written  in this  wonderful forum...but  anyway i  will go ahead....

My  problem: When i try to logout i only have the chance to "end session", the old menu with  multiple choices that appeared before now never ever show up...so i just can shut down ubuntu turning off my computer  manually.

It'd be nice that someone help me in this stupid  issue.

Tx in advance.

---

### Post by super on 2006-01-02
ya that's kinda weird.
why not just logout and select shutdown from the 'actions' menu of the login manager.

---

### Post by scaine on 2006-01-02
Sounds like you installed Ubuntu, then installed KDE.  Or vice versa?

Which do you use?  You should still have all the various options when you choose System/Logout in Gnome (log out, shutdown, restart, suspend, etc).

---

### Post by labrie on 2006-01-02
I didnt install kde, and yes is pretty weird  this  issue....but now that you mention kde maybe  i uninstall gnome and install kde so i can logout properly...

anyway tx for the attention.:D

---

### Post by scaine on 2006-01-02
You'll likely have the same problem.  If you run Gnome, you must run GDM to get the logout options.  If you run KDE, you must KDM to get the logout options.

There is a dpkg-reconfigure command that you can run that will allow you to change your display manager, but I don't know enough about it to comment.

Sorry I can't be any more help.

Good luck.

---

