---
title: "Local .desktop file problems"
date: 2007-01-25
forum: Desktop Environments
---

### Post by naylorjs on 2007-01-25
Hi Folks

I'm developing a lovely application which works wonderfully. The main control programs are installed with their .desktop files stored in /usr/share/applications and their icons in /usr/share/pixmaps, so far so good.

I need to be able to install local applications which are only visible to the currently logged on user. According to the standard Gnome documentation this should be possible. The .desktop file should be installed in ~/.local/share/applications. If I do this then the new applications doesn't appear. The .desktop file is fine as I copied it to /usr/share/applications and it appeared in the menu and operated as expected.

This behaviour is seen in Ubuntu 6.10 and is also true for 6.06, which is the first version of Ubuntu that I have used. The Gnome reference for the paths is [http://www.gnome.org/learn/admin-guide/latest/menustructure-desktopentry.html](http://www.gnome.org/learn/admin-guide/latest/menustructure-desktopentry.html)

Any help would be appreciated, or is it a bug in Ubuntu?

Jonathan

---

