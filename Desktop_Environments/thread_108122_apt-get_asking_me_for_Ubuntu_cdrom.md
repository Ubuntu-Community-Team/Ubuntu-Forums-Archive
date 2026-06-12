---
title: "apt-get asking me for Ubuntu cdrom"
date: 2005-12-25
forum: Desktop Environments
---

### Post by TallMatthew on 2005-12-25
I'm trying to install mailx so I can send email from the command-line (and cron), and when I try to apt-get the package, it asks me for the cdrom, which seems strange.

mhempel@linuxshuttle:/root$ sudo apt-get install mailx
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  liblockfile1 postfix
Suggested packages:
  postfix-mysql postfix-pgsql postfix-ldap postfix-pcre
Recommended packages:
  resolvconf
The following NEW packages will be installed:
  liblockfile1 mailx postfix
0 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/1075kB of archives.
After unpacking 2580kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Media change: please insert the disc labeled
 'Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)'
in the drive '/cdrom/' and press enter

I see this same behavior trying to install postfix and other packages as well.  If anyone could explain why, I'd appreciate it.

Matt

---

### Post by 23meg on 2005-12-25
Because they're on the Ubuntu CD, which is given priority over the repositories. Comment out the line for the CD in your /etc/apt/sources.list and you can fetch them from the repositories.

---

### Post by kaamos on 2005-12-25
The packages are in the cdrom, and apt is trying by default to install them from there so you don't have to download anything.

If you do not wish to use the cdrom:
```
sudo gedit /etc/apt/sources.list
```
And comment out (with #) the line with the cd. Then run:
```
sudo apt-get update
```
And you're good to go..

---

### Post by TallMatthew on 2005-12-25
Thanks.  

Nothing like moving to a new distro to make you feel like a newbie again.

---

