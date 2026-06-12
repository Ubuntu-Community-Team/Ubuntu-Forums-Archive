---
title: "restoring the system"
date: 2011-02-27
forum: Dell Ubuntu Support (CLOSED)
---

### Post by acetrix on 2011-02-27
hi i am in a tight situation i am running ubuntu 10.04 when i accidentally typed the command:
 sudo apt-get REMOVE fakeroot automake1.9 build-essential libpango1.0-dev libgtk2.0-dev libgconf2-dev libglitz-glx1-dev librsvg2-dev libglade2-dev libxcomposite-dev subversion libtool libgtop2-dev python-gtk2-dev libgnome-menu-dev libgnomeui-dev libgnomevfs2-dev intltool libxml2-dev libglitz1-dev libcairo2 libdbus-1-dev libgtop2-7 libgnomevfs2-0 libgnomeui-0 librsvg2-2 python-feedparser libasound2-dev libsdl1.2-dev libdbus-glib-1-dev libgstreamer-plugins-base0.10-dev libgstreamer0.10-dev libgstreamer0.10-0 pidgin-dev libpurple-dev

it started deleting all my system files so i decided to reboot but it was too late ALMOST all files were deleted it booted in terminal mode and i basically couldn't reverse the command as sudo was messed up.
is there a way of restoring the system before that time or something of the sort.thanx in advance.

---

### Post by bryncoles on 2011-02-28
I might be stupid in asking this, but did you try typing 

```
sudo apt-get install fakeroot automake1.9 build-essential libpango1.0-dev libgtk2.0-dev libgconf2-dev libglitz-glx1-dev librsvg2-dev libglade2-dev libxcomposite-dev subversion libtool libgtop2-dev python-gtk2-dev libgnome-menu-dev libgnomeui-dev libgnomevfs2-dev intltool libxml2-dev libglitz1-dev libcairo2 libdbus-1-dev libgtop2-7 libgnomevfs2-0 libgnomeui-0 librsvg2-2 python-feedparser libasound2-dev libsdl1.2-dev libdbus-glib-1-dev libgstreamer-plugins-base0.10-dev libgstreamer0.10-dev libgstreamer0.10-0 pidgin-dev libpurple-dev
```

Into the terminal when you rebooted?  Surely that would start putting the files back?

If it errors on you, try ```
sudo dpkg --configure -a
``` This apparently checks all the packages you have installed, and if it finds any which are misconfigured it fixes them (I think). 

Plan c is this: ```
sudo apt-get install -f
```  Which tries to reinstall missing essential packages. 

Plan D is this: ```
sudo apt-get update && sudo apt-get upgrade
```

Let me know if any of them work!

---

### Post by bryncoles on 2011-02-28
Also... (if you don't mind me asking) *how* did you accidentally type that command?  Did someone online give you dodgey advice?

---

