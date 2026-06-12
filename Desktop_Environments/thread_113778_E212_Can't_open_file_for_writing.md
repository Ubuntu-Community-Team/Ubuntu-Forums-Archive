---
title: "E212: Can't open file for writing"
date: 2006-01-07
forum: Desktop Environments
---

### Post by s0c0 on 2006-01-07
E212: Can't open file for writing

Thats the error I get when I try to write any file using vim.  It opens a read-only copy always even when I am logged into root.  It also says something about not being able to open a temporary file for writing.

What caused this?  I was trying to change the system run-level to 3 because I didn't want to automatically boot into the GUI.  So I editted the /etc/inittab file.  I think I changed the wrong setting though.  I changed a section that reads similiar to this:

> # Boot-time system configuration/initialization script...
# This is run first when booting in emergency (-b) mode
si::sysinit:/etc/init.d/rc5

I changed it to rc3.  After rebooting all hell broke loose.  This has to be the worst mistake I've made on a linux box.  Of course afterwards I noticed the option I meant to change was just above this. :( 

Please help.  I really don't want to re-install.  I already tried booting into recovery console, but I still receive the same error.  Google hasn't yielded much, but I'm going to keep looking.

---

### Post by s0c0 on 2006-01-07
bump

I believe there may be a way to fix this using Knoppix.  Thanks for the help guys.

---

### Post by schilcha on 2006-01-07
[QUOTE=s0c0]E212: Can't open file for writing

Thats the error I get when I try to write any file using vim.  It opens a read-only copy always even when I am logged into root.  It also says something about not being able to open a temporary file for writing.
[/QUOTE]

Sounds as if your disk was full (probably not your case) or the disk is mounted read-only. Use the command "mount" to see the options of the currently mounted disks.

Now, for the cause of the whole mess... I can't really tell. Anyways, here's the beginning of my inittab-file:
```

# /etc/inittab: init(8) configuration.
# $Id: inittab,v 1.91 2002/01/25 13:35:21 miquels Exp $

# The default runlevel.
id:2:initdefault:

# Boot-time system configuration/initialization script.
# This is run first except when booting in emergency (-b) mode.
si::sysinit:/etc/init.d/rcS

# What to do in single-user mode.
~~:S:wait:/sbin/sulogin

```

To change the default runlevel, change "id:2:initdefault:" to e.g. "id:3:initdefault:" to switch to runlevel 3 by default. I suggest to boot into rescue mode (if that still works) or to boot off a CD (knoppix / ubuntu-livecd / ...), mount the root-partition and edit/correct /etc/inittab.

Good Luck!

---

### Post by schilcha on 2006-01-07
... Forgot one more thing ... If you don't want X11 to be started at boot, you could also remove it from the runlevel-definition. Try ```
sudo update-rc.d -f gdm remove
```

---

### Post by coopergillan on 2006-03-29
I am getting the same E212 error whenever I try to create new files in my apache server directory. No matter how I try save either .html or .php files, I always get this error, even when using :x! or :w!

Any ideas? Thanks for any help!

---

