---
title: "How do I uninstall these?"
date: 2006-07-11
forum: Desktop Environments
---

### Post by ardchoille on 2006-07-11
I have the following installed:

1) cupsys
2) cupsys-bsd
3) cupsys-client
4) bluez-cups
5) cupsys-driver-getenprint
6) gnome-cups-manager
7) libcupsimage2
8) libcupsys2

I do not own any printers and I don't really see the need in having these installed and having to update them when I don't have a printer. When I mark them for complete removal, ubuntu-desktop and xubuntu-desktop are also marked for removal but I do not want to uninstall the desktop meta packages.

How do I uninstall the above numbered items without uninstalling the desktop meta packages?

Is it safe to uninstall the desktop meta packages and still be able to update everything I have installed?

---

### Post by Titus A Duxass on 2006-07-11
I think that you may encounter the same problems as I did when trying to streamline an installation.

I ended up doing a server install and building up from there.

---

### Post by mcman42 on 2006-07-11
Well, man, do you really need to uninstall them so desperately? I haven't got any printer either but I keep those. I dont think that they take up too much space, why uninstaling them then? They probably can be removed ithout affcting the desktop package but it will be problematic.

---

### Post by Titus A Duxass on 2006-07-11
I understand ardchoille, the fact that unwanted stuff is installed in the first place makes make seethe.

You are correct it will be problematic, especially anything to do with CUPS.

You'll probably find a load of stuff for HP printers as well.

---

### Post by mlind on 2006-07-11
It's a catch-22 situation, you either keep the cups packages or uninstall ubuntu-desktop meta package, which is safe thing to do.

---

### Post by ardchoille on 2006-07-11
Ok, let's go a different way. Is it possible to "dpkg --purge --don't-remove-deps packagename" or something like that so that I can safely remove cups and it's deps one by one and not remove ubuntu-desktop?

---

### Post by mlind on 2006-07-11
> **ardchoille said:**
> Ok, let's go a different way. Is it possible to "dpkg --purge --don't-remove-deps packagename" or something like that so that I can safely remove cups and it's deps one by one and not remove ubuntu-desktop?

It will break package dependencies and APT won't like it. There's no harm of removing ubuntu-desktop meta package. It's just there to provide you a set of  installed applications. Removing ubuntu-desktop doesn't remove anything else.

Just install it back before upgrading.

---

### Post by ardchoille on 2006-07-11
> **mlind said:**
> It will break package dependencies and APT won't like it. There's no harm of removing ubuntu-desktop meta package. It's just there to provide you a set of  installed applications. Removing ubuntu-desktop doesn't remove anything else.

Just install it back before upgrading.

And that will install all of the cups things back into the system won't it?
And then I'd have to uninstall cups, bluez utils, hp stuff, etc all over again.

I think I'll just re-install Ubuntu using the server install and then install things as I need them as Titus A Duxass suggested. Thank you all for the help and information.

---

### Post by mlind on 2006-07-11
> **ardchoille said:**
> And that will install all of the cups things back into the system won't it?
And then I'd have to uninstall cups, bluez utils, hp stuff, etc all over again.

I think I'll just re-install Ubuntu using the server install and then install things as I need them as Titus A Duxass suggested. Thank you all for the help and information.

You don't have to install that ubuntu-desktop package ever back if you want. And that upgrading means dist upgrading, like Breezy --> Dapper.
I've removed that package long time a ago, and will install it back only when Breezy comes out, so all desktop dependencies are upgraded too.

Removing cups and and other stuff ain't that hard either,
```

sudo aptitude purge *package_to_remove*

```

---

### Post by ardchoille on 2006-07-11
> **mlind said:**
> You don't have to install that ubuntu-desktop package ever back if you want. And that upgrading means dist upgrading, like Breezy --> Dapper.
I've removed that package long time a ago, and will install it back only when Breezy comes out, so all desktop dependencies are upgraded too.

Removing cups and and other stuff ain't that hard either,
```

sudo aptitude purge *package_to_remove*

```

Oh, well that makes things better. I'll just remove cups and ubuntu-desktop. I always install a new Ubuntu version from CD/DVD so I never dist-upgrade anyway.

Thank you for explaining this :)

---

