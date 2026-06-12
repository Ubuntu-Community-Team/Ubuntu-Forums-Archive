---
title: "Installing icons and .desktop files for applications"
date: 2010-08-06
forum: Desktop Environments
---

### Post by Joey The Saint on 2010-08-06
Hey all,

I'm really not sure where to post this and I can't imagine the question hasn't already been asked but my googling hasn't turned up a particularly clear answer.  Please redirect me if I'm in the wrong place.

I have an autoconf-based project that I'm packaging for Ubuntu and it doesn't currently install an icon or have a .desktop file.  I've got an icon for it now and wrote up a .desktop file but I can't find a good example of where I should install them to in my make install stage.  This is currently what I've added to my Makefile.am:

```

EXTRA_DIST = ardbico.xpm \
             ../resources/ardb.desktop

icondir = $(icondir)/icons

icon_DATA = ardbico.xpm

Applicationsdir = $(datadir)/gnome/apps/Games

Applications_DATA = ../resources/ardb.desktop
```

which works well enough for doing the base install, but, of course, my icon ends up in /usr/share/icons/ when really I thought it should land in /usr/share/app-install/icons and my .desktop file should probably go to /usr/share/app-install/desktop.  I looked at gnome-games and sudoku as examples of how this should be done (hoping a smallish application that seems to behave properly would be a good place to look) but I couldn't find anything that actually had a .desktop except GNOME Robots, so I'm still none the wiser.  Any pointers would be great.

Update: turns out that the .desktop file had a single error in the Categories section that was causing it to not appear in the menus properly.  desktop-file-validate pointed me right at at, I fixed that and everything else was just a matter of specifying the paths where I wanted stuff to land.

---

