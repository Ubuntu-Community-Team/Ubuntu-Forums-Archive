---
title: "random frequent gnome semi-freezes"
date: 2007-12-11
forum: Desktop Environments
---

### Post by Cooner on 2007-12-11
I've recently developed a problem with gnome/firefox/totem in Gutsy (recently upgraded from Dapper) where I get a "soft freeze", with the following results:

-- clicking fails, but moving the mouse works fine,
-- typing in the active window works, but things like Alt-Tab (change active window), Shift-Alt-Arrow (switch desktops) fail.  I am still able to navigate using shortcuts such as Alt-F4 to kill the program, Alt to access menus, Tab/Return to navigate links, and the like.
-- Ctrl-Alt-Bkspace kills the x.org

Often there is a clear "culprit program"... generally firefox, though also totem.  If I kill this program, things revert to healthy immediately.

It comes and goes... in totem, for instance, it tends to "freeze" when I try to add a file.  Tabbing to cancel, hitting Enter then brings things back to life happily.

I initially suspected an issue with my configuration files in /home from dapper remaining in my upgrade to gutsy (I kept my /home partition through the upgrade).  Therefore, I created a new user, signed in with this new user, and tried to break it.  It took a while, but eventually the freeze returned for the new user immediately after an add of the flash plugin.  So I removed the flash plugin from both users.  This initially seemed to fix things, but the freezes eventually returned.  In fact, a kill and/or logout of the xserver helps for a while, but the freezes eventually return.  Once they're back, they happen every time I open firefox/totem.  Attached is an strace of a freeze that happened immediately after opening firefox, and was promptly fixed when I Alt-F4 killed firefox.

This is driving me batty... any advice would be appreciated!

---

### Post by Cooner on 2007-12-13
partial bump, partial update...

after doing a fresh install, just to clean out all my old config files and the like, I'm still seeing this.

It seems to only be happening **after** doing a sleep/wakeup cycle.  No trace of any issues in kern.log/dmesg/etc regarding the sleep, and acipd's logfile looks normal.

---

