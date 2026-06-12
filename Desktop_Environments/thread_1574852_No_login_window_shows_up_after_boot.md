---
title: "No login window shows up after boot"
date: 2010-09-14
forum: Desktop Environments
---

### Post by tonyatvt on 2010-09-14
Everything looks fine until when the login screen should show up but doesn't. The cursor is there and can move.
I can switch to terminal by *ctl-alt-F**, and login. After *gdm stop* and *startx*, gnome is back but only in fail safe mode, with non-movable non-resizable window, only one workspace, and cursor is a black cross...

I ever met a similar case before, which comes to the login screen but it keeps reloading after entering password. Finally got solved by run *sudo apt-get install --reinstall ubuntu-desktop* in terminal. This time it doesn't work anymore.

Please help, I really can't bear reinstall the system because I configured many programs. Thank you!

---

