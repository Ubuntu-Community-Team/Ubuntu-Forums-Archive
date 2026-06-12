---
title: "Could not start the X server"
date: 2008-12-29
forum: General Help
---

### Post by lukemack on 2008-12-29
Hi,

I'm getting the following error on boot in Ubuntu 8.10 Desktop:


Could not start the X
server (your graphical environment)
due to some internal error.
Please contact your system administrator
or check your syslog to diagnose.
In the meantime this display will be
disabled. Please restart GDM when
the problem is corrected.

I can then drop out to prompt. However, trying anything as root/sudo gives me the error that the file system is read-only so I can't change any files or run any commands which change files. I believe the problem occurred after installing VirtualBox 2.1 and rebooting.

I have tried:

Booting into recovery mode and running xfix - no change.
Removing /etc/X11/ config files - I cant do this because the filesystem is read only (even as root)

Please can someone tell me how to get the filesystem back so that it is writable and / or give me some advise on how to get gdm back?

The syslog contains errors relating to gdmgreeter but i cant paste the syslog as I am not on that machine.

Thanks!

---

### Post by lukemack on 2008-12-29
running fsck -y resolved this for me. I'm not 100% sure if it was VirtualBox that caused the problem or the laptop not shutting down correctly at some point.

I suspect that linux booted the filesystem in read-only mode and gdm was trying to write to the filesystem on boot after the install of VirtualBox but thats a best guess.

---

### Post by vahnx on 2009-01-03
I've almost given up on Linux all together because of things like this. Random errors for no reason at all. Windows just works. It may be M$, but Windows doesn't have random crashes as much as Linux.

---

### Post by cactusgal on 2009-01-04
You could try the following that worked for me. In the terminal type:

sudo apt-get remove xserver-xorg

when that's finished type:

sudo apt-get install xserver-xorg

I tried quite a few other things, including editing my xorg.conf, before I decided to do this and now everything is back to normal and running fine. I hope this works for you.

Regards,
cactusgal

---

