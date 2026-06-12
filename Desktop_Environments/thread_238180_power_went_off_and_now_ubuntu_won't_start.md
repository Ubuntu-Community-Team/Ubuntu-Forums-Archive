---
title: "power went off and now ubuntu won't start"
date: 2006-08-17
forum: Desktop Environments
---

### Post by syd2o2 on 2006-08-17
The power went of while the comp was on, and when I switched it back on, ubuntu won't start again.
Ubuntu goes through start up process, then it comes to starting X, nvidia logo flashes a few times, but X doesn't start. I get message on the screen. something like this:
Failed to start X server. It is likely not set up corectly.
And it offers to view X server output.
This is the errors reported in that output:

error openning security file /etc/X11/xserver/SecurityPolicy
(EE) Prelnit returned NULL for "configured mouse"
>Warning Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
> Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
(EE) xf86Open Serial: cannont open device /dev/wacom
     no such file or directory 
Error openning /dev/wacom: no such file or directory

#And then this about /dev/wacom is repetad 6 more times until (rest of the output):

No core pointer
Fatal server error.
Failed to initialize core devices.

I don't even get to command line. After I close window with that output, it just stands there, with the last line of text being:

*Running local boot scripts (/etc/rc.local)

Can anybody help me to fix ubuntu?

I did setup Logitech mouse using a howto found on this forum (requiring to change the mouse section in xorg.conf). And I have nvidia drivers installed (with automatix).

---

### Post by syd2o2 on 2006-08-17
I booted the system with ubuntu live cd, and replaced xorg.conf with a backup, and now it's working again.

---

