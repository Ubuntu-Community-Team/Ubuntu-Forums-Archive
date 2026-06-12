---
title: "Metacity settings do nothing, not running Compiz"
date: 2009-06-12
forum: Desktop Environments
---

### Post by manekineko2 on 2009-06-12
I followed the tutorial here:
[http://my.opera.com/locksley90/blog/2008/05/12/assigning-keyboard-shortcuts-in-ubuntu]("http://my.opera.com/locksley90/blog/2008/05/12/assigning-keyboard-shortcuts-in-ubuntu")
and the tutorial here:
[http://tombuntu.com/index.php/2008/11/14/metacity-compositing-effects-in-ubuntu-810/]("http://tombuntu.com/index.php/2008/11/14/metacity-compositing-effects-in-ubuntu-810/")
in order to customize my Metacity.  Unfortunately, none of the changes made in gconf-editor seem to have any effect at all.

I'm pretty certain I must be running Metacity, since I'm using an 8.10 Intrepid install, with proprietary drivers disabled.  Under gconf-editor, I even went to /desktop/gnome/applications/window_manager, and changed the keys current and default (both of which were originally blank), to have the values /usr/bin/metacity.

However, somehow my keyboard shortcuts and compositing effects aren't enabled.

Can anyone give any advice on how to debug this problem?

---

### Post by manekineko2 on 2009-06-14
I've tried to resolve this problem by updating to Jaunty, but the issues still remain.  I've even gone into Synaptic and removed Compiz to make sure I'm not using it, and none of my Metacity customizations seem to work.

Could anyone point me in the direction I should look to resolve this?

---

### Post by manekineko2 on 2009-06-14
In case anyone else has this problem, I resolved it by entering in the appropriate changes using gconftool-2 from the command line.  No idea why gconf-editor gui wasn't doing it, even though it was showing the changes graphically, but this fixed it.

---

