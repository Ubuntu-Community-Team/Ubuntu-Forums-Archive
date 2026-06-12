---
title: "desktop in XFCE?"
date: 2005-06-19
forum: Desktop Environments
---

### Post by kerinin on 2005-06-19
there are a couple threads about this, but they aren't working so i'll start a new one.

i'm using XFCE, but i'd like to have a working desktop (ie, with icons showing the contents of ~/Desktop on it).  i've been running nautilus -n & every time i start a new session but this is sort of annoying.  is there some way to have XFCE do this for me automatically?

i've tried adding 'nautilus -n &' to ~/.xsession and /etc/xdg/xfce4/xinitrc but that doesn't work because i'm still using the gnome session manager.  i've tried saving the session settings but it doesn't show up when i log back in.

also, i tried going through [http://www.ubuntuforums.org/showthread.php?t=31310](this) HOWTO to make XFCE autostart, but i don't want to uninstall gdm and it didn't work.  any way to keep gdm on my system but load into XFCE by default?

thanks!

---

### Post by psychicdragon on 2005-06-19
Why are you using the gnome session manager as opposed to the xfce one?

---

### Post by az on 2005-06-20
Rox provides a pinboard which does the job of a desktop.   you can change the background image and put symlinks on it.  Dran and drop.  Works well...  Rox is faster than Nautilus, basically, if you are starting up Nautilus, where is the advantage of running XFCE4?

rox -p=1


To make your session XFCE, change the session that is default in gdm, before you log in.  It will ask you if you want to keep this as a default.  Say yes.

---

### Post by kerinin on 2005-06-20
the problem with ROX is that it only shows icons which you explicitly put on the pinboard.  it won't display the contents of a folder (ie the ~/Desktop folder), and it won't update links as files are deleted.  well, maybe it will and i just don't know how to do it ;)

how do i change to the XFCE session manager?

---

### Post by psychicdragon on 2005-06-20
When you're looking at gdm click on "Sessions" and select an Xfce session. Once Xfce starts up run nautilus and it will take over your desktop. Then select Quit from the Xfce menu and make sure you check "Save session for future logons." Next time you start Xfce nautilus should be on your desktop.

---

