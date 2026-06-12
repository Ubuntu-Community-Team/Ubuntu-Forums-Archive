---
title: "System freezes at login"
date: 2008-01-23
forum: Desktop Environments
---

### Post by ElSean on 2008-01-23
Hi, I'm running 7.4 on a AMD 64 X2 (64-bit ubuntu)

Whenever it boots, it will sit at the logon screen for Gnome for about 5 seconds, during this time I can start logging in or do nothing and then it will freeze.   Then the screen distorts itself.  The entire system is non-responsive, no caps lock light on keyboard, no mouse.  I have to do a hard reset.  I can't even get 
into a tty.

I thought it might be hardware related, but when I boot the 7.4 live CD, I can run everything perfectly fine.  I am also running 7.4 on a second identical hardware machine and have no problems.

I have tried the following:

Booting with each of the following extensions, none fix the problem:
pci=nopci
acpi=off
acpi=noirq
pci=noacpi

I have tried editing the xorg.conf file to comment out the "load dri" line.  Did not fix it.  I even reset the xorg.conf file to its default settings.

The closest thing to an error I can find in the logs is this:

"Bogus length in write keyboard desc, expected 5068, got 5072"

I've tried booting without a keyboard or mouse plugged in, still freezes and distorts the screen.

---

