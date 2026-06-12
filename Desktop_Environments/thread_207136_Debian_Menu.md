---
title: "Debian Menu?"
date: 2006-07-01
forum: Desktop Environments
---

### Post by Mike_N on 2006-07-01
Ya know how Automatix installs the "Debian Menu" that shows more app's then the standard menu? Well, how can i get that, without using Automatix?

Thanks, Mike

---

### Post by llamakc on 2006-07-01
```

ken@dothan:~$ apt-cache show menu
Package: menu
Priority: optional
Section: universe/admin
Installed-Size: 1532
Maintainer: Bill Allombert <ballombe@debian.org>
Architecture: i386
Version: 2.1.27
Depends: libc6 (>= 2.3.4-1), libgcc1 (>= 1:4.0.2), libstdc++6 (>= 4.0.2-4), dpkg (>= 1.10)
Suggests: gksu | kdebase-bin | sux
Filename: pool/universe/m/menu/menu_2.1.27_i386.deb
Size: 376506
MD5sum: 054648b9fdc883b1a09e48dd3346e824
Description: generates programs menu for all menu-aware applications
 Debian menu keeps transparently the menus in the different
 window-managers in sync with the list of installed programs.
 .
 Debian menu relies on a list of menu entries provided by programs
 and a list of menu-methods provided by window-managers and other
 menu-aware applications.
 .
 Menu provides system-level and user-level configuration and overrides
 for both menu entries and menu-methods.
Bugs: mailto:ubuntu-users@lists.ubuntu.com
Origin: Ubuntu

```

So it is in the universe repository. Enable that if it is not and then use the apt frontend of your choice.

From the terminal:

sudo apt-get install menu

will do the trick for ya.

---

### Post by cyhk on 2008-01-22
I installed the Debian Menu through Synaptic, using the menu-xdg package.  I then restarted the X environment with Ctrl+Alt+Backspace.  The Debian Menu doesn't show under Applications menu.  

Any ideas on how to get it to show?  Oh, this is on Feisty.

Thanks.

---

### Post by smartboyathome on 2008-01-22
Right click on your Application/Places/System menus, and select edit menus. Click the check box next to "Debian" in the list that pops up.

---

