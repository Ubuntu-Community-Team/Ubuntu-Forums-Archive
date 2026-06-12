---
title: "Persmission denied in /usr/sbin"
date: 2006-07-15
forum: Desktop Environments
---

### Post by tzulberti on 2006-07-15
Unpacking xinetd (from .../xinetd_1%3a2.3.14-0ubuntu1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/xinetd_1%3a2.3.14-0ubuntu1_i386.deb (--unpack):
 unable to create `./usr/sbin/xinetd': Permission denied

I am installing xinetd. But i have also the same problem when installing flash-non-free plugin...

---

### Post by jordilin on 2006-07-15
Please explain what process do you take to install packages. Take into account that you must have root access so if you are running apt-get install you have to write sudo apt-get install nameofpackage. If you are running synaptic it should have asked you for a password, and there would be no problem. If in fact, you are running synaptic, then there must be another problem.

---

### Post by taurus on 2006-07-15
You need to use sudo if you want to install anything to your machine...

```

sudo dpkg -i <package_name>.deb

```

---

### Post by tzulberti on 2006-07-15
I have used synaptic and apt (with sudo). But with both am I getting the same error message.

---

### Post by jordilin on 2006-07-15
There must be something else than just a "Permission Denied". Take a look at the permissions of this folder and let us know. Take a look as well at the /var/log/messages file to see if it says something, just in case.

---

### Post by Ramses de Norre on 2006-07-15
```
**.**/usr/sbin/xinetd
```
I think the period "." in front of the path is weird.. but I'm not sure what to conclude from it or how to solve it.

---

### Post by tzulberti on 2006-07-15
This are the permissions of that folder:
drwxr-xr-x   2 root     root         8192 Jul 14 06:04 sbin

And this is the full message that it appears when i do apt-get install xinetd:
tzulberti@ubuntu32:/usr$ sudo apt-get install xinetd
Reading package lists... Done
Building dependency tree... Done
The following NEW packages will be installed:
  xinetd
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/131kB of archives.
After unpacking 356kB of additional disk space will be used.
(Reading database ... 103627 files and directories currently installed.)
Unpacking xinetd (from .../xinetd_1%3a2.3.14-0ubuntu1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/xinetd_1%3a2.3.14-0ubuntu1_i386.deb (--unpack):
 unable to create `./usr/sbin/xinetd': Permission denied
dpkg-deb: subprocess paste killed by signal (Broken pipe)

I have looked at /var/log/messages but nothing appears.Maybe i should reinstall ubuntu, becuase I have many errors (even one with the top command)...

---

