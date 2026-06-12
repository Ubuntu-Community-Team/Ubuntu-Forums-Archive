---
title: "can not remove broken package, no answer found"
date: 2006-01-29
forum: Desktop Environments
---

### Post by quazar on 2006-01-29
**Problem solved**

I've tried to install a package called: xandros-parport-2.6.9-x1_1.0_i386.deb because my LPT port was not working. However, I got some errors. Now synaptic does not start anymore, and removing of this package seems to be impossible.

This is how it started:

:~$ sudo dpkg -i xandros-parport-2.6.9-x1_1.0_i386.deb
(Reading database ...
dpkg: serious warning: files list file for package `xandros-parport-2.6.9-x1' missing, assuming package has no files currently installed.
84702 files and directories currently installed.)
Preparing to replace xandros-parport-2.6.9-x1 1.0 (using xandros-parport-2.6.9-x1_1.0_i386.deb) ...
mv: cannot stat `/lib/modules/2.6.9-x1/kernel/drivers/parport/parport_pc.ko': No such file or directory
dpkg: error processing xandros-parport-2.6.9-x1_1.0_i386.deb (--install):
 subprocess pre-installation script returned error exit status 1
mv: cannot stat `/etc/devices/parport_pc.ko.nonpatched': No such file or directory
dpkg: error while cleaning up:
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 xandros-parport-2.6.9-x1_1.0_i386.deb

and this is the response I get when removing:
:~$ sudo apt-get remove xandros-parport-2.6.9-x1_1.0_i386.deb
Reading package lists... Done
Building dependency tree... Done
E: The package xandros-parport-2.6.9-x1 needs to be reinstalled, but I can't find an archive for it.

~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree... Done
E: The package xandros-parport-2.6.9-x1 needs to be reinstalled, but I can't find an archive for it.

sudo dpkg -r xandros-parport-2.6.9-x1
dpkg: error processing xandros-parport-2.6.9-x1 (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 xandros-parport-2.6.9-x1

The synaptic error: E: The package xandros-parport-2.6.9-x1 needs to be reinstalled, but I can't find an archive for it. E: Internal error opening cache (1). Please report.

This is stated in /var/lib/dpkg: 
Package: xandros-parport-2.6.9-x1
Status: install reinstreq half-installed
Priority: extra
Section: base
Version: 1.0





Is there an other way to remove this package?

edit: **sudo dpkg --remove --force-all xandros-parport-2.6.9-x1 solved the problem** :)

---

