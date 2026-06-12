---
title: "sudo apt-get install fluxbox"
date: 2006-06-13
forum: Desktop Environments
---

### Post by guitardan311 on 2006-06-13
first off, might i say that ubuntu is one very cool distrobution. i just recently went back to using linux as my primary OS because i will be studying the unix/linux field of IT in college. i never have used debian or apt on any of my machines (more used to portage on gentoo) and i keep getting an error message when i try and install an application.

using fluxbox as an example because that is what i want to use as my desktop manager. in the terminal, however, i get this message:
> Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package fluxbox


pretty much any package i try does this.

---

### Post by aysiu on 2006-06-13
Follow these instructions: [http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources) and then do ```
sudo aptitude update
sudo aptitude install fluxbox
```

---

### Post by guitardan311 on 2006-06-13
thanks man, worked perfectly. whats the differance between using the aptitude command over apt-get?

---

### Post by aysiu on 2006-06-13
[QUOTE=guitardan311]thanks man, worked perfectly. whats the differance between using the aptitude command over apt-get?[/QUOTE] Here's the difference. 

**Aptitude**: ```
username@ubuntu:~$ sudo aptitude update && sudo aptitude install kword
Password:
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
Get:1 http://security.ubuntu.com dapper-security Release.gpg [189B]
Get:2 http://archive.ubuntu.com dapper Release.gpg [189B]
Get:3 http://archive.ubuntu.com dapper-updates Release.gpg [189B]
Get:4 http://security.ubuntu.com dapper-security Release [27.0kB]
Get:5 http://archive.ubuntu.com dapper-backports Release.gpg [189B]
Hit http://archive.ubuntu.com dapper Release
Get:6 http://archive.ubuntu.com dapper-updates Release [27.0kB]
Ign http://packages.freecontrib.org dapper Release.gpg
Ign http://packages.freecontrib.org dapper Release
Get:7 http://archive.ubuntu.com dapper-backports Release [19.6kB]
Ign http://packages.freecontrib.org dapper/free Packages
Get:8 http://security.ubuntu.com dapper-security/main Packages [14.4kB]
Hit http://archive.ubuntu.com dapper/main Packages
Get:9 http://archive.ubuntu.com dapper/restricted Packages [4571B]
Hit http://archive.ubuntu.com dapper/main Sources
Get:10 http://archive.ubuntu.com dapper/restricted Sources [1478B]
Hit http://archive.ubuntu.com dapper/universe Packages
Hit http://archive.ubuntu.com dapper/universe Sources
Get:11 http://archive.ubuntu.com dapper/multiverse Packages [95.2kB]
Ign http://packages.freecontrib.org dapper/non-free Packages
Get:12 http://security.ubuntu.com dapper-security/restricted Packages [14B]
Get:13 http://security.ubuntu.com dapper-security/main Sources [3593B]
Get:14 http://security.ubuntu.com dapper-security/restricted Sources [14B]
Get:15 http://security.ubuntu.com dapper-security/universe Packages [3762B]
Get:16 http://security.ubuntu.com dapper-security/universe Sources [14B]
Ign http://packages.freecontrib.org dapper/free Sources
Ign http://packages.freecontrib.org dapper/non-free Sources
Get:17 http://archive.ubuntu.com dapper/multiverse Sources [46.6kB]
Hit http://packages.freecontrib.org dapper/free Packages
Get:18 http://archive.ubuntu.com dapper-updates/main Packages [10.2kB]
Get:19 http://archive.ubuntu.com dapper-updates/restricted Packages [14B]
Get:20 http://archive.ubuntu.com dapper-updates/main Sources [9006B]
Get:21 http://archive.ubuntu.com dapper-updates/restricted Sources [14B]
Get:22 http://archive.ubuntu.com dapper-backports/main Packages [14B]
Get:23 http://archive.ubuntu.com dapper-backports/restricted Packages [14B]
Get:24 http://archive.ubuntu.com dapper-backports/universe Packages [14B]
Get:25 http://archive.ubuntu.com dapper-backports/multiverse Packages [14B]
Hit http://packages.freecontrib.org dapper/non-free Packages
Hit http://packages.freecontrib.org dapper/free Sources
Hit http://packages.freecontrib.org dapper/non-free Sources
Fetched 263kB in 2s (89.0kB/s)
Reading package lists... Done
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following NEW packages will be automatically installed:
  kspread kword-data libwv2-1c2
The following NEW packages will be installed:
  kspread kword kword-data libwv2-1c2
0 packages upgraded, 4 newly installed, 0 to remove and 0 not upgraded.
Need to get 6613kB of archives. After unpacking 18.9MB will be used.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
Get:1 http://archive.ubuntu.com dapper/main kspread 1:1.5.0-0ubuntu9 [2276kB]
Get:2 http://archive.ubuntu.com dapper/main libwv2-1c2 0.2.2-5 [225kB]
Get:3 http://archive.ubuntu.com dapper/main kword-data 1:1.5.0-0ubuntu9 [1590kB]
Get:4 http://archive.ubuntu.com dapper/main kword 1:1.5.0-0ubuntu9 [2522kB]
Fetched 6613kB in 45s (146kB/s)
Selecting previously deselected package kspread.
(Reading database ... 110852 files and directories currently installed.)
Unpacking kspread (from .../kspread_1%3a1.5.0-0ubuntu9_i386.deb) ...
Selecting previously deselected package libwv2-1c2.
Unpacking libwv2-1c2 (from .../libwv2-1c2_0.2.2-5_i386.deb) ...
Selecting previously deselected package kword-data.
Unpacking kword-data (from .../kword-data_1%3a1.5.0-0ubuntu9_all.deb) ...
Selecting previously deselected package kword.
Unpacking kword (from .../kword_1%3a1.5.0-0ubuntu9_i386.deb) ...
Setting up kspread (1.5.0-0ubuntu9) ...

Setting up libwv2-1c2 (0.2.2-5) ...

Setting up kword-data (1.5.0-0ubuntu9) ...

Setting up kword (1.5.0-0ubuntu9) ...

username@ubuntu:~$ sudo aptitude remove kword
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
[b]The following packages are unused and will be REMOVED:
  kspread kword-data libwv2-1c2
The following packages will be REMOVED:
  kword[/b]
0 packages upgraded, 0 newly installed, 4 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 18.9MB will be freed.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
(Reading database ... 111678 files and directories currently installed.)
Removing kword ...
Removing kspread ...
Removing kword-data ...
Removing libwv2-1c2 ...
username@ubuntu:~$
``` **Apt-get**: ```
username@ubuntu:~$ sudo apt-get update && sudo apt-get install kword
Get:1 http://security.ubuntu.com dapper-security Release.gpg [189B]
Get:2 http://archive.ubuntu.com dapper Release.gpg [189B]
Get:3 http://archive.ubuntu.com dapper-updates Release.gpg [189B]
Get:4 http://archive.ubuntu.com dapper-backports Release.gpg [189B]
Hit http://security.ubuntu.com dapper-security Release
Hit http://archive.ubuntu.com dapper Release
Hit http://archive.ubuntu.com dapper-updates Release
Hit http://security.ubuntu.com dapper-security/main Packages
Hit http://archive.ubuntu.com dapper-backports Release
Hit http://archive.ubuntu.com dapper/main Packages
Hit http://archive.ubuntu.com dapper/restricted Packages
Hit http://archive.ubuntu.com dapper/main Sources
Ign http://packages.freecontrib.org dapper Release.gpg
Hit http://security.ubuntu.com dapper-security/restricted Packages
Hit http://security.ubuntu.com dapper-security/main Sources
Hit http://security.ubuntu.com dapper-security/restricted Sources
Hit http://archive.ubuntu.com dapper/restricted Sources
Hit http://archive.ubuntu.com dapper/universe Packages
Hit http://archive.ubuntu.com dapper/universe Sources
Hit http://archive.ubuntu.com dapper/multiverse Packages
Hit http://archive.ubuntu.com dapper/multiverse Sources
Ign http://packages.freecontrib.org dapper Release
Hit http://archive.ubuntu.com dapper-updates/main Packages
Hit http://archive.ubuntu.com dapper-updates/restricted Packages
Hit http://archive.ubuntu.com dapper-updates/main Sources
Hit http://archive.ubuntu.com dapper-updates/restricted Sources
Hit http://security.ubuntu.com dapper-security/universe Packages
Hit http://security.ubuntu.com dapper-security/universe Sources
Ign http://packages.freecontrib.org dapper/free Packages
Ign http://packages.freecontrib.org dapper/non-free Packages
Ign http://packages.freecontrib.org dapper/free Sources
Ign http://packages.freecontrib.org dapper/non-free Sources
Hit http://packages.freecontrib.org dapper/free Packages
Hit http://archive.ubuntu.com dapper-backports/main Packages
Hit http://packages.freecontrib.org dapper/non-free Packages
Hit http://packages.freecontrib.org dapper/free Sources
Hit http://archive.ubuntu.com dapper-backports/restricted Packages
Hit http://archive.ubuntu.com dapper-backports/universe Packages
Hit http://archive.ubuntu.com dapper-backports/multiverse Packages
Hit http://packages.freecontrib.org dapper/non-free Sources
Fetched 4B in 2s (2B/s)
Reading package lists... Done
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  kspread kword-data libwv2-1c2
Suggested packages:
  koffice-doc-html
The following NEW packages will be installed:
  kspread kword kword-data libwv2-1c2
0 upgraded, 4 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/6613kB of archives.
After unpacking 18.9MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Selecting previously deselected package kspread.
(Reading database ... 110852 files and directories currently installed.)
Unpacking kspread (from .../kspread_1%3a1.5.0-0ubuntu9_i386.deb) ...
Selecting previously deselected package libwv2-1c2.
Unpacking libwv2-1c2 (from .../libwv2-1c2_0.2.2-5_i386.deb) ...
Selecting previously deselected package kword-data.
Unpacking kword-data (from .../kword-data_1%3a1.5.0-0ubuntu9_all.deb) ...
Selecting previously deselected package kword.
Unpacking kword (from .../kword_1%3a1.5.0-0ubuntu9_i386.deb) ...
Setting up kspread (1.5.0-0ubuntu9) ...

Setting up libwv2-1c2 (0.2.2-5) ...

Setting up kword-data (1.5.0-0ubuntu9) ...

Setting up kword (1.5.0-0ubuntu9) ...

username@ubuntu:~$ sudo apt-get remove kword
Reading package lists... Done
Building dependency tree... Done
[b]The following packages will be REMOVED:
  kword[/b]
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives.
After unpacking 7000kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 111678 files and directories currently installed.)
Removing kword ...
username@ubuntu:~$ 
``` See the difference? (Hint: it's in bold)

---

### Post by Patrick-Ruff on 2006-06-13
completely different install service in general eh? (never heard of it though).

---

### Post by aysiu on 2006-06-13
I highly recommend *aptitude* over *apt-get*, but the ```
sudo aptitude update
``` command is critical to it functioning properly.

---

