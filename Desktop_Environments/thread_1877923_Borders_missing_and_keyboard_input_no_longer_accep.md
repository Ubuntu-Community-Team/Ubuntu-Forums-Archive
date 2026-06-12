---
title: "Borders missing and keyboard input no longer accepted"
date: 2011-11-08
forum: Desktop Environments
---

### Post by peyre on 2011-11-08
I'm running Xubuntu 11.10; I upgraded from 11.04.  It's been running great, but suddenly when I fired it up this morning, the title bars of regular-decorated windows (Thunar, Pidgin, GIMP, etc.) are missing.  So I can't minimize, maximize, and close them with the usual icons in the corner, and can't drag windows around the screen.  Also, Web browsers won't accept keyboard input in the address bar or Google search bar.  Also, my task list at the bottom of the screen is missing and it doesn't respond to Alt-Tab, so I can't switch between programs easily.  I thought aha, maybe it's just a settings change I need to make or something, so I went into Settings Manager: and both the Window Manager and Window Manager Tweaks come up blank (see attached).

Help please!  I'm reduced to sending this from my kids' Windows machine.  ;)

---

### Post by vangop on 2011-11-08
Hi!
This happens from time to time.No idea why, nothing in logs. 
I have this if I press log out, and nothing happens for a while, then it does logs out, but the next logon is screwed up.
Fix: delete ~/.cache
Login from virtual terminal and rm -rf ~/.cache

---

### Post by peyre on 2011-11-09
Hey, that worked!  I hit Ctrl-Alt-F2, logged in, and entered "rm -rf ~/.cache" (I forget if I had to use sudo in front of it), rebooted, and all's well again.  Thanks!

---

### Post by TrevP on 2011-11-09
The problem is that your window manager (xfwm4) has not started. If there is a problem at shutdown (it's normally obvious because the computer seems to freeze at shutdown for around 30 seconds), xfwm4 does not start at the next boot. On my system, monitor blanking or the startup of a screensaver will cause this issue at shutdown or logout.

rm -r ~/.cache/sessions will work, but if you get the problem on a regular basis, it becomes a bit of a pain. The workaround that I use is to include xfwm4 in the startup programs so that it is always restarted on login.

---

