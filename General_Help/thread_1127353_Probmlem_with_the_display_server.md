---
title: "Probmlem with the display server"
date: 2009-04-16
forum: General Help
---

### Post by shmulike on 2009-04-16
Hi,

I'm new to Ubuntu.
I have installed it on my HP laptop (dual boot with winXP using WUBI.exe)

Everything was working fine, but then my compiz-fusion halted the laptop, so I had to close the laptop with the power button.

When I restarted ubuntu I got some sort of "blue-screen" message saying:
"The display server has been shut down about 6 time in the last 90 seconds. It is likely that something bad is going on...."


What should I do? is there any way to fix this or do I need to reinstall ubuntu?

---

### Post by cariboo on 2009-04-16
Start in recovery mode, press esc at the grub menu and select recovery mode, once at the menu select xfix. Once xfix is finished select resume and continue on to your desktop. Ocne you desktop is loaded you will have to re-activate the restricted drivers.

Jim

---

### Post by shmulike on 2009-04-17
Thanks for the help, but this doesn't work... :(

After running the xfix I get:
dpkg-error: parse error, in file `/var/lib/dpkg/status' near line 1: file name `' must be followd be a colon
/usr/sbin/dpkg-reconfigure: xorg-server is not installed

How should I proceed?

---

