---
title: "KDE session Restart/Shut Down buttons missing"
date: 2007-05-19
forum: Desktop Environments
---

### Post by Neuralgia on 2007-05-19
I have Ubuntu as default, and a KDE session, XFCE session, and the 3 of them (Ub, Kub, Xub) with XGL also.

Both Gnome sessions have, all of the buttons to: Log out, switch user, restart, shut down.

Both XFCE session also have them.

Only KDE session don't. The only button I get is "Log out"

Every once in a while I like to chande Desktop Environments, and not having thos buttons with KDE, is a little annoying.

Any help?

---

### Post by Obor on 2007-05-19
Its because GDM is your default display manager (both gnome and xfce use GDM).

It's a confirmed [bug in kdebase]("https://bugs.launchpad.net/ubuntu/feisty/+source/kdebase/+bug/64695"). KDE is not talking to GDM...

You can change your display manager to KDM 
```
sudo dpkg-reconfigure gdm
```
and then you will have those buttons in KDE but they will be missing in gnome and Xfce :(

The best is probably to use
shutdown
```
sudo shutdown -h now
```
restart
```
sudo shutdown -r now
```
And wait till they fix the bug.

---

