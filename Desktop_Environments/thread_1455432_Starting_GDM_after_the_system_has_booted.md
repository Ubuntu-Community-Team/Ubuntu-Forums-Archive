---
title: "Starting GDM after the system has booted?"
date: 2010-04-15
forum: Desktop Environments
---

### Post by houldsworth1 on 2010-04-15
I need to run my Ubuntu system 'headless' (no screen or keyboard) due to space.  Originally I would run it with a screen attached and use VNC for remote access.  But as soon as I took the screen off the machine failed to boot.

Following  advice I found here I changed the value for GRUB_CMDLINE_LINUX_DEFAULT in /etc/default/grub to an empty string and changed /etc/X11/default-display-manager to be empty (it was previously /usr/sbin/gdm). The machine will now boot without a screen attached and I can now access the machine using putty from my windows box but I have no GUI anymore.  

This is fine for about 90% of my needs but the GUI is still useful for some functions so I was wondering if there is a way I can kick that off once the machine has booted. 

I tried running sudo /usr/sbin/gdm but received the following errors:

[INDENT]:~$ sudo /usr/sbin/gdm
gdm-binary[10134]: WARNING: Unable to find users: no seat-id found
gdm-binary[10134]: WARNING: GdmDisplay: display lasted 0.803781 seconds
gdm-binary[10134]: WARNING: GdmDisplay: display lasted 0.800900 seconds
gdm-binary[10134]: WARNING: GdmDisplay: display lasted 0.802454 seconds
gdm-binary[10134]: WARNING: GdmDisplay: display lasted 0.797240 seconds
gdm-binary[10134]: WARNING: GdmDisplay: display lasted 0.800098 seconds
gdm-binary[10134]: WARNING: GdmDisplay: display lasted 0.802786 seconds
gdm-binary[10134]: WARNING: GdmLocalDisplayFactory: maximum number of X display failures reached: check X server log for errors
[/INDENT]

Any ideas on how I can start this when needed and then run VNC to access the system?

Many thanks!

---

