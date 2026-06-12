---
title: "Unity toolbar crashes after enabling descktop cube"
date: 2011-05-02
forum: Desktop Environments
---

### Post by Shreshtha on 2011-05-02
I did fresh installation of 11.04 Ubuntu on IntelQ6600 with ATI graphics card.

I opened settings->CompizConfig Setting manager and enabled Desktop cube. It suggested to disable Desktop wall and Desktop Unity plugin (recommended by Ubuntu).

After that 
1 Tool bar at top crashed (no menu item seen, garbled pixels)
2. Alt-tab stopped working
3. Only way to close any window is Alt+F4.

How to reset back to unity?

Thanks in advance.

PS: 10.10 was best so far in Ubuntu.

---

### Post by ralfthewise on 2011-05-03
Check out:
[http://www.omgubuntu.co.uk/2011/04/compiz-cube-natty/](http://www.omgubuntu.co.uk/2011/04/compiz-cube-natty/)


As for getting back to a working system, this is what I did:

WARNING!!!  The instructions below will probably delete all your settings, so only follow them if you want to do so.  I was on a fresh install so I didn't care.

1.  Reboot and then prior to logging in, press Ctrl+Alt+F1.
2.  Login to the console and then delete config stuff:
  rm -rf .adobe/ .cache/ .compiz/ .config/ .dbus/ .dmrc .esd_auth .gconf* .gnome2* .gtk-bookmarks .gvfs/ .ICEauthority .local/ .macromedia/ .mplayer/ .nautilus/ .profile
3.  Press Ctrl+Alt+F7 to switch back to the login screen and reboot.

---

### Post by dansang on 2011-06-09
To get unity back to previous working order, reboot in ubuntu mode from log in.

Open a terminal Crt-Alt  + T then type:

```
ccsm
```

reselect unity plugin in the compiz manager window and reboot > login

your previous unity desktop should be restated!!

---

### Post by pritam_par on 2011-08-10
check out the link. This issue is solved 
[http://ubuntuforums.org/showthread.php?t=1747045](http://ubuntuforums.org/showthread.php?t=1747045)

---

