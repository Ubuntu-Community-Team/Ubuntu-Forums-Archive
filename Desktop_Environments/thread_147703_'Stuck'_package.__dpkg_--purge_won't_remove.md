---
title: "'Stuck' package.  dpkg --purge won't remove"
date: 2006-03-20
forum: Desktop Environments
---

### Post by darkpixel on 2006-03-20
*sigh*
Just when you start to think you're not a noob at linux anymore...


A long while back I installed the package 'firestarter' on Breezy.
Yesterday I was cleaning up all the 'junk' I had installed and tried to remove firestarter.

Here's the process and error:

root@quark:~# dpkg --purge firestarter
(Reading database ... 141827 files and directories currently installed.)
Removing firestarter ...
Purging configuration files for firestarter ...
dpkg: error processing firestarter (--purge):
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 firestarter
root@quark:~#

I poked around the documentation for dpkg, dselect, synaptic, etc... and I can't seem to find a way to remove that package.  I'm guessing the maintainer screwed up the package.  So how do I go about removing it?

I know where the files are themselves, so I can remove them manually--but how do I get the package out of dpkg?

---

### Post by mlind on 2006-03-20
Did you try removing firestarter using apt-get remove --purge?

---

### Post by az on 2006-03-20
The purge switch only remove the debconf information.  You don<t really need to purge most packages to remove them.

First, try to remove the package without the purge option.

If that doesn't work, try

sudo dpkg --clear-avail
and then try again to remove it.

---

### Post by darkpixel on 2006-03-25
[QUOTE=mlind]Did you try removing firestarter using apt-get remove --purge?[/QUOTE]

The result:
root@quark:~# apt-get remove --purge firestarter
Reading package lists... Done
Building dependency tree... Done
Package firestarter is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 37 not upgraded.
root@quark:~#

The package still shows up as having 'residual config' in synaptic and still shows up with a dpkg -l.

root@quark:~# dpkg -l | grep firestarter
pc  firestarter                                      1.0.3-1.1ubuntu1            gtk program for managing and observing your firewall

---

### Post by darkpixel on 2006-03-25
[QUOTE=azz]The purge switch only remove the debconf information.  You don<t really need to purge most packages to remove them.

First, try to remove the package without the purge option.

If that doesn't work, try

sudo dpkg --clear-avail
and then try again to remove it.[/QUOTE]

This still gives me the same error:

root@quark:~# dpkg --clear-avail
root@quark:~# dpkg --purge firestarter
(Reading database ... 142012 files and directories currently installed.)
Removing firestarter ...
Purging configuration files for firestarter ...
dpkg: error processing firestarter (--purge):
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 firestarter
root@quark:~#

---

