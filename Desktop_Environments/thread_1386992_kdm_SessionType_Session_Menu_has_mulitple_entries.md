---
title: "kdm SessionType Session Menu has mulitple entries"
date: 2010-01-21
forum: Desktop Environments
---

### Post by rickyrockrat on 2010-01-21
Hi all,
I just installed a bazillion window managers for fun and entertainment (it's kinda cool to see how they all are different), then restarted the KDM session. When I clicked on the SessionType, they almost filled my screen!

Then I noticed many of them are duplicated. The problem is there are several directories where the entries for this menu are installed.

Take a look at /etc/kdex/kdm/kdmrc, (x being 2,3,4 depending on the kde version) and look for the SessionsDirs. Mine was not set, so the default is /usr/share/xsessions,/var/lib/menu-xdg/xsessions,/usr/share/apps/kdm/sessions

What I found is that the duplications were from some appearing in the menu-xdg and in the /usr/share/xsessions.  The fix is to go to one of them (I went to /usr/share/xsessions) and move them all to some directory (I called mine dups).  Then re-start the X server (menu->restart Xserver) or Alt-E.

Obviously, if you want to *add* a window manager, you would create a .desktop file for it, i.e. copy and modify an existing one.
Cheers!!

---

