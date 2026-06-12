---
title: "Is it possible to ignore a broken package?"
date: 2005-10-03
forum: Desktop Environments
---

### Post by SilverTab on 2005-10-03
I downloaded and installed kftpgrabber (a secure FTP client for KDE), and when I installed it I got some depandancy errors, but the app was still installed and it's running smoothly so I would like to keep it...

Problem is: Synaptic is telling me that I have a broken package (kftpgrabber) and wont install anything unless I uninstall it.....

via apt-get I get the same problem if I try to install something I get:
```
Building dependency tree... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
kftpgrabber: Depends: libc6 (>= 2.3.2.ds1-21) but 2.3.2.ds1-20ubuntu13 is to be installed
Depends: libfontconfig1 (>= 2.3.0) but 2.2.3-4ubuntu7 is to be installed
Depends: libidn11 (>= 0.5.13) but 0.5.2-3 is to be installed
Depends: libqt3c102-mt (>= 3:3.3.4) but 3:3.3.3-7ubuntu3 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
```

(and I was only trying to install Glade here so there's no link with kftpgrabber)

My question is: If i'm satisfied with the package...is there a way to "trick" synaptic into thinking that its not a broken package???

---

### Post by Zelut on 2005-10-03
Well if you did "Smart Upgrade" with Synaptic or apt-get -f install it should include the broken or missing packages.  I don't think it'd auto-uninstall your program, just include whats needed.  Have you given that a try?

---

### Post by SilverTab on 2005-10-03
if I use apt-get -f install  I get:

Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... Done
The following packages will be REMOVED:
  kftpgrabber
0 upgraded, 0 newly installed, 1 to remove and 82 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 1905kB disk space will be freed.
Do you want to continue [Y/n]?


its always trying to remove it...and I want to keep it...

---

### Post by az on 2005-10-03
[QUOTE=SilverTab]if I use apt-get -f install  I get:

its always trying to remove it...and I want to keep it...[/QUOTE]


It is not built for ubuntu.  Find the source packages (.dsc .diff .orig.tar.gz) and compile it from source, or find an ubuntu version  (Has it been backported?)

You cannot keep this package on your system.  You either have to change the package or change your system.

---

