---
title: "cant install artwiz-cursor package in breezy...help please"
date: 2005-11-11
forum: Desktop Environments
---

### Post by deepclutch on 2005-11-11
Hello
I use Breezy and its great OS :razz: .i am not able to install artwiz-cursor by apt-get and manually as its giving an error message:
```

root@ubuntu:/home/prakash/Downloads# dpkg -i artwiz-cursor_1.3-2_all.deb
(Reading database ... 57934 files and directories currently installed.)
Unpacking artwiz-cursor (from artwiz-cursor_1.3-2_all.deb) ...
Leaving `diversion of /usr/X11R6/lib/X11/fonts/misc/cursor.pcf.gz to /usr/X11R6/lib/X11/fonts/misc/cursor.pcf.gz-artwiz by artwiz-cursor'
update-alternatives: Cannot find alternative `/etc/X11/cursors/core.theme'.

dpkg: error processing artwiz-cursor_1.3-2_all.deb (--install):
 subprocess pre-installation script returned error exit status 2
Errors were encountered while processing:
 artwiz-cursor_1.3-2_all.deb

```

what should i do to get artwiz-cursor,i installed xfonts-artwiz etc...In my Sarge 3.1 r0a artwiz-cursor is working.....please help..... :)

---

### Post by deepclutch on 2005-11-11
Please help me.... :desperate: :???:

---

### Post by deepclutch on 2005-11-12
I have reported this as a bug.but some body can help me to get alternative way for installing artwiz-cursor.please help me pinpoint error.

```

prakash@ubuntu:~$ sudo apt-get install artwiz-cursor
Reading package lists... Done
Building dependency tree... Done
The following NEW packages will be installed:
  artwiz-cursor
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/8644B of archives.
After unpacking 102kB of additional disk space will be used.

Preconfiguring packages ...
(Reading database ... 58246 files and directories currently installed.)
Unpacking artwiz-cursor (from .../artwiz-cursor_1%3a1.3-2_all.deb) ...
Leaving `diversion of /usr/X11R6/lib/X11/fonts/misc/cursor.pcf.gz to /usr/X11R6/lib/X11/fonts/misc/cursor.pcf.gz-artwiz by artwiz-cursor'
update-alternatives: Cannot find alternative `/etc/X11/cursors/core.theme'.

dpkg: error processing /var/cache/apt/archives/artwiz-cursor_1%3a1.3-2_all.deb (--unpack):
 subprocess pre-installation script returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/artwiz-cursor_1%3a1.3-2_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
prakash@ubuntu:~$ sudo apt-get upgrade artwiz-cursor
Reading package lists... Done
Building dependency tree... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded

```

---

### Post by deepclutch on 2005-11-13
Help me Pyagg's

---

### Post by deepclutch on 2005-11-18
:dumb:

---

### Post by ubbby on 2006-01-24
Hehe! Welcome to the arrogant Ubuntu community! There are no answer for your questions and bugreports here. But if you receive answers, these will look, like this: "Try to solve this probleme yourselve alone. We will fix it for the NEXT release". Oh yeah, this is the famous long-term support of the human-warmy Ubuntu community. It would be better to switch to SuSE or Gentoo.

---

### Post by deepclutch on 2006-03-08
Any body to help?

---

### Post by deepclutch on 2006-03-12
whatta hell?Yet to fix the bug..went and reported @t Launchpad ~~mess,no replies./.f'
sa/fsd
:mad: :mad: :mad: :mad: :mad:

---

### Post by deepclutch on 2006-04-05
now lately they found this is an old package..got reported as a bug#4211
those who upgraded from hoary to breezy will not seems to have problems..but it will not working with dapper Xorg 7
read more:
[https://launchpad.net/distros/ubuntu/+source/xfonts-artwiz/+bug/4211](https://launchpad.net/distros/ubuntu/+source/xfonts-artwiz/+bug/4211)

---

