---
title: "GNOME Display Manager (gdm) - it is not the default..."
date: 2006-03-03
forum: Desktop Environments
---

### Post by OffHand on 2006-03-03
Hi

After I removed KDE my GDM won't start.

GNOME Display Manager (gdm); it is not the default display manager.

Anyone know what I should do?

---

### Post by fuscia on 2006-03-03
if you can get to synaptic and reinstall gdm, any time i have switched display managers, i have been prompted to choose a default. best i can do - sorry.

---

### Post by OffHand on 2006-03-03
re-installed without any luck.
I also get this error message before the login window opens: 

cannot open file /usr/share/apps/kdm/themes/kubuntu

Any help is appreciated! 

Note to self: don't start fooling around at 5 am  :D

---

### Post by cjazz on 2006-03-04
Please try

sudo dpkg-reconfigure gdm

---

### Post by OffHand on 2006-03-04
[QUOTE=cjazz]Please try

sudo dpkg-reconfigure gdm[/QUOTE]

That worked. Thanks a lot  :)
Another small question.... In my login screen I am still able to select KDE although I uninstalled it. Is there any way to remove it from the options?
Not a big deal tho but if it's easy to change....

---

### Post by cjazz on 2006-03-04
[QUOTE=subsonic_shadow]In my login screen I am still able to select KDE although I uninstalled it. Is there any way to remove it from the options?
Not a big deal tho but if it's easy to change....[/QUOTE]

I'm not sure why that would be happening. Did you uninstall KDE with apt-get remove or Synaptic, or was this done manually?

The only thing I can suggest offhand is to move the KDE file in /usr/share/xsessions to another name or location. Of course, this would have to be done as root. I suggest move instead of delete, for safety's sake.

---

