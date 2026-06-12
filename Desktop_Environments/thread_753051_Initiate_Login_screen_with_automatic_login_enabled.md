---
title: "Initiate Login screen with automatic login enabled"
date: 2008-04-12
forum: Desktop Environments
---

### Post by Meson on 2008-04-12
I'm on a single user machine with full disk encryption so I felt it was perfectly reasonable to enable automatic login.  But what I would like to know is if there is a hotkey or something to call the login screen during boot.  This is in case I want to login to a different session or I'm having some sort of problem with xorg etc...

---

### Post by sardion on 2008-04-13
Its not really possible to do this cleanly.

The only thing I can think of is to use a different runlevel and set up the gnome start script in the new runlevel to not use autologin.  Then in grub set up a new config for that runlevel.  You cna effectively pick on boot whether to use autologin.

That said, its probly much easier to just let it autologin and then choose logout from the "shutdown" menu dialog to getthe session selector.

---

