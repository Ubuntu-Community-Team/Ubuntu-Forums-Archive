---
title: "E: Internal error opening cache (from synaptic)"
date: 2005-10-31
forum: Desktop Environments
---

### Post by npodges on 2005-10-31
a bit ago, i tried installing JRE. i didnt think it was available from synaptic, so i downloaded it from sun. they only had an rpm, so i converted that to a deb, and tryed instlaling from that. i dont remember how far it got me, but i know it didnt work.
more significantly tohugh, everytime i try to run synaptic, i get this:
```
E: The package jre needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.
```
any ideas?

---

### Post by npodges on 2005-11-05
any ideas *yet?*

---

### Post by willowhisp on 2006-10-07
Try reinstalling jre with either aptitude or by downloading and installing the debian package.

Edit: Woops didn't notice how old this thread was....:oops: But, sense I'm having a similar problem, does anyone know how to deal with that sort of error?

---

### Post by anroy on 2007-03-01
Rather than create a new thread I thought I will add to this one, since I got the same problem and it is a very critical one.

Basically I cannot use Synaptic now, after a failure trying to install a printer driver for the Brother Multi-office printer/fax MFC-8820JN.

I downloaded:
mfc8820jlpr-1.1.2-1.i386.deb
from Brother's site here (it is Japanese)
[http://solutions.brother.co.jp/linux/lpr_driver.html](http://solutions.brother.co.jp/linux/lpr_driver.html)

I then tried to install it from the right-click context menu "Open with GDebi Package Installer".

Installation failed.  I got the following error.
[IMG]http://img402.imageshack.us/img402/9378/screenshotgdebigtknr4.png[/IMG]


Now, when I go to Synaptic I get the message below, and Synaptic doesn't open.
> E: The package mfc8820jlpr needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.

If I try to remove it with
sudo dpkg -r mfc8820jlpr

I get this:
> dpkg: error processing mfc8820jlpr (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 mfc8820jlpr


So it is a bit of a crisis situation.  All I want right now is to be able to use synaptic again, I can take my time on the driver.

Any advice?

Thanks!

---

### Post by anroy on 2007-03-02
I was able to solve it using the information in these two helpful threads by bss1234 and Jheric.

[http://ubuntuforums.org/showthread.php?p=1981359](http://ubuntuforums.org/showthread.php?p=1981359)
[http://ubuntuforums.org/showthread.php?t=252922](http://ubuntuforums.org/showthread.php?t=252922)

They also pointed me to similar threads on the Debian forum.  It seems like Brother printer drivers are causing tremendous grief to Linux users.  This goes beyond not just working, but disabling a major part of the OS like Synaptic.  This is not a light matter.

What I did was to first comment out references to:
/etc/init.d/lpd
from files
/var/lib/dpkg/info/mfc8820jlpr.postrm
/var/lib/dpkg/info/mfc8820jlpr.postinst

Then I ran:
sudo apt-get remove --purge mfc8820jlpr
and got the following (successful) result.
> Reading package lists... Done
Building dependency tree... Done
The following packages will be REMOVED:
  mfc8820jlpr*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? Y
(Reading database ... 90904 files and directories currently installed.)
Removing mfc8820jlpr ...
Purging configuration files for mfc8820jlpr ...
dpkg - warning: while removing mfc8820jlpr, directory `/usr/local/Brother' not empty so not removed.
dpkg - warning: while removing mfc8820jlpr, directory `/usr/local' not empty so not removed.

Hopefully this will help someone in the future, and also serve as a warning that Brother printer drivers are risky to your system.

---

