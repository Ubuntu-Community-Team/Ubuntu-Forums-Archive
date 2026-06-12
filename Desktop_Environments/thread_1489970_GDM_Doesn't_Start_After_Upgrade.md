---
title: "GDM Doesn't Start After Upgrade"
date: 2010-05-21
forum: Desktop Environments
---

### Post by linuxpyro on 2010-05-21
I just upgraded from 9.10 to 10.04.  While it seemed to go fine, GDM won't start.  (Instead the Plymouth bootloader just displays the splash screen continuously.)  I can get in through a virtual terminal, but starting GDM via the init script does not do anything.  I also tried this:

```

me@host:~$ sudo gdm
**
ERROR:gdm-settings-direct.c:157:gdm_settings_direct_get_boolean: assertion failed: (entry != NULL)
Aborted

```

I tried running sudo dpkg-reconfigure gdm, but this did not change anything.  Logged in from the virtual terminal I can run startx and get the desktop, but obviously I would like to have the login manager working.  Anyone else having this problem?

---

### Post by linuxpyro on 2010-05-21
Alright, all I had to do was reinstall GDM and purge the config files, and now it works.  

If you have this problem, just do this:

```

sudo aptitude purge gdm

```

It'll probably tell you it needs to remove some other packages, just do that and then reinstall them along with GDM.

---

