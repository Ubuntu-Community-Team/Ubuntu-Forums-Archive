---
title: "Whereis /boot/grub/menu.lst in Lucid"
date: 2010-06-03
forum: Desktop Environments
---

### Post by SOG420 on 2010-06-03
I would like to boot into a console in Lucid and after searching the web and forums I can't find how to do This .  I've tried looking for the grub file as well as the menu.lst file
Thanks

---

### Post by BoneKracker on 2010-06-03
I don't use Ubuntu, but it's my understanding that your latest release (Lucid Lynx) used GRUB 2.  GRUB 2 has a different arrangement of its configuration files, and there's no "menu.lst" anymore.

I would advise you to search forum for a link to Ubuntu-specific documentation on GRUB2 before making any changes.

---

### Post by SOG420 on 2010-06-03
Such A basic Solution 
[http://ubuntuforums.org/showthread.php?t=1195275]("http://ubuntuforums.org/showthread.php?t=1195275")

---

### Post by oldfred on 2010-06-03
GRUB 2  has three main parts plus a boot loader installed to the MBR:

   1. /etc/default/grub - the file containing GRUB 2 menu settings.
   2. /etc/grub.d/ - the directory containing GRUB 2 menu creating scripts.And a place for totally custom entries 40_custom.
   3. /boot/grub/grub.cfg - the GRUB 2 configuration file, not editable.

General info:
The Grub 2 Guide (formerly Grub 2 Basics)
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

### Post by SOG420 on 2010-06-04
OK I edited Grub file /etc/default/grub to:
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT=""
GRUB_CMDLINE_LINUX=""

#Uncomment to disable graphical terminal (grub-pc only)
GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_LINUX_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"
I get a non quiet boot but no command line. What am I doing wrong?

---

### Post by hictio on 2010-06-04
Shouldn't you have to stop the Gnome Display Manager as well? Something on the lines like:
```

sudo /etc/init.d/gdm stop

```

---

