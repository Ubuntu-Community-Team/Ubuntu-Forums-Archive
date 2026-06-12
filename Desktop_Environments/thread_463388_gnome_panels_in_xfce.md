---
title: "gnome panels in xfce"
date: 2007-06-03
forum: Desktop Environments
---

### Post by dbodner on 2007-06-03
I just recently made the switch over to xfce, and for the most part love it. There's one thing I'm missing though. In gnome, you could place two panels down on the bottom of the script, one above the other. I know in xfce you can add a new panel, make it freely moveable, and widen it. But when you have something opened full screen, the bottom of the app overlaps with the panel, whereas in gnome it doesn't.

I guess my questions are the following:
- Is there any way to add a second panel to the bottom in xfce (above the bottom panel, not over top) in which applications won't overlap?
- If not, I tried adding 'gnome-panel &' to my startup, and running both gnome and xfce panels together. This actually works well, and allows me to have my 2 gnome panels on the bottom, and use xfce for the rest. Problem is, both gnome and xfce try to take over the desktop. gnome starts up, sets itself to the desktop, then xfce tries and says there's already something using it. I then have to go into Settings > Desktop Settings in xfce and check "Allow Xfce to manage the desktop" to get my xfce desktop back. Is there any way to startup gnome panels without having it manage the desktop as well?

Thanks.

---

### Post by pbw on 2007-06-03
I don't use either desktop anymore, but have you tried killall -9 xfce4-panel and then starting gnome-panel? Don't see why that wouldn't work.

Pretty sure i did that quite awhile ago when i ran xgl on xfce

edit: you might also want to run gconftool -t bool /apps/nautilus/preferences/show_desktop -s false to prevent nautilus from trying to take over managing the desktop.

No idea, but this might help as well. [http://assente.altervista.org/it/use_thunar_as_default_gnome_file_manager/](http://assente.altervista.org/it/use_thunar_as_default_gnome_file_manager/)

---

### Post by dbodner on 2007-06-03
> edit: you might also want to run gconftool -t bool /apps/nautilus/preferences/show_desktop -s false to prevent nautilus from trying to take over managing the desktop.

That was actually just about exactly what I was looking for.  Thanks!

---

