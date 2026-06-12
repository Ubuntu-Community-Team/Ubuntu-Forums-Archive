---
title: "Package Problem-Can't apt-get install (or remove) anything--PLEASE HELP!"
date: 2006-02-08
forum: Desktop Environments
---

### Post by jose0425 on 2006-02-08
I**'m having a problem with a deb package. I downloaded s3savage-driver_1.1.23t-1_i386.deb  from **[**here**]("http://www.probo.com/timr/savage40.html#download"). **it was supposed to be the drivers of my Video Adapter. But when trying to install it i got this:**


sudo dpkg -i s3savage-driver_1.1.23t-1_i386.deb
Selecting previously deselected package s3savage-driver.
(Reading database ... 111030 files and directories currently installed.)
Preparing to replace s3savage-driver 1.1.23t-1 (using s3savage-driver_1.1.23t-1_i386.deb) ...
Unpacking replacement s3savage-driver ...
dpkg: dependency problems prevent configuration of s3savage-driver:
 s3savage-driver depends on xserver-xfree86 (>= 4.1.0); however:
  Package xserver-xfree86 is not installed.
dpkg: error processing s3savage-driver (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 s3savage-driver


[B]ok. It didn't matter to me until i found out that i couldn't also download anything else using apt-get because of this:
[/B]
sudo apt-get install skype
Reading package lists... Done
Building dependency tree... Done
E: The package s3savage-driver needs to be reinstalled, but I can't find an archive for it.

**If i try to remove the broken package (s3savage-driver) then i get this:**

sudo apt-get remove s3savage-driver
Reading package lists... Done
Building dependency tree... Done
E: The package s3savage-driver needs to be reinstalled, but I can't find an archive for it.

**or this:**
sudo dpkg -r s3savage-driver
dpkg: error processing s3savage-driver (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 s3savage-driver

**I've also tried other methods such as purge and reinstall but they don't work also. when trying to reinstall the package i get this:**

sudo dpkg -i s3savage-driver_1.1.23t-1_i386.deb

(Reading database ... 111030 files and directories currently installed.)
Preparing to replace s3savage-driver 1.1.23t-1 (using s3savage-driver_1.1.23t-1_i386.deb) ...
Unpacking replacement s3savage-driver ...
dpkg-divert: rename involves overwriting `/usr/X11R6/lib/modules/drivers/savage_drv.o' with
  different file `/usr/share/s3savage-driver/diversions/savage_drv.o', not allowed
dpkg: warning - old post-removal script returned error exit status 2
dpkg - trying script from the new package instead ...
dpkg-divert: rename involves overwriting `/usr/X11R6/lib/modules/drivers/savage_drv.o' with
  different file `/usr/share/s3savage-driver/diversions/savage_drv.o', not allowed
dpkg: error processing s3savage-driver_1.1.23t-1_i386.deb (--install):
 subprocess new post-removal script returned error exit status 2
dpkg-divert: rename involves overwriting `/usr/X11R6/lib/modules/drivers/savage_drv.o' with
  different file `/usr/share/s3savage-driver/diversions/savage_drv.o', not allowed
dpkg: error while cleaning up:
 subprocess post-removal script returned error exit status 2
Errors were encountered while processing:
 s3savage-driver_1.1.23t-1_i386.deb

**so i remove the broken files with sudo rm. but the problem still continues. CAN ANYONE HELP ME PLEASE?**

---

### Post by oakz on 2006-02-08
try:

$ sudo apt-get -f update

---

### Post by jose0425 on 2006-02-08
Thanks! it worked!

---

