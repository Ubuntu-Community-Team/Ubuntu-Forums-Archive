---
title: "screen resolution too low in 12.04"
date: 2012-06-27
forum: Desktop Environments
---

### Post by garydale on 2012-06-27
I recently migrated a system from 32bit hardware to 64bit. This meant a fresh install except for /home. I also copied some user account information from the old /etc/passwd, shadow and group files to the new ones.

The first big problem I hit was the screen resolution. The monitor is an old Compaq P1100 that can handle some pretty high resolutions but Ubuntu won't let it. It insists that it can only do 1024x768@60Hz or less.

I copied the old /etc/X11/xorg.conf file over since it contains the frequency information for the monitor but that didn't help.

I used cvt to generate a modeline for a reasonable setting and used xrandr to put it in place. After that I was able to use System Settings | Displays to set the new resolution but after logging out and back in (or rebooting), I get the message about the CRT resolutions not being possible.

I'm currently using the xrandr commands in a script that is setuid root to set the resolution when I log in. However, that is clumsy and the login screen still flickers thanks to the low refresh rate.

This is using the open source radeon driver, which is the only real option for this system.

Any ideas on how I can get Ubuntu to actually handle the refresh information in xorg.conf?

---

