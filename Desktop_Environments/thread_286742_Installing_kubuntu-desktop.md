---
title: "Installing kubuntu-desktop"
date: 2006-10-28
forum: Desktop Environments
---

### Post by sasteeleuk on 2006-10-28
I did a fresh install of Ubuntu which was successful. I typed sudo kubuntu-desktop and got an error. I ran the following command

sudo apt-get install -f
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libavahi-compat-libdnssd1
The following NEW packages will be installed:
  libavahi-compat-libdnssd1
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
3 not fully installed or removed.
Need to get 0B/29.6kB of archives.
After unpacking 102kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
(Reading database ... 133820 files and directories currently installed.)
Unpacking libavahi-compat-libdnssd1 (from .../libavahi-compat-libdnssd1_0.6.13-2ubuntu2_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libavahi-compat-libdnssd1_0.6.13-2ubuntu2_i386.deb (--unpack):
 trying to overwrite `/usr/lib/libdns_sd.so.1', which is also in package bonjour
Errors were encountered while processing:
 /var/cache/apt/archives/libavahi-compat-libdnssd1_0.6.13-2ubuntu2_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

Any ideas, I am getting a error message 'Error: BrokenCount > 0' on my update manager which I can't get rid off?

Cheers
Shawn

---

### Post by GStubbs43 on 2006-10-28
Type
```
sudo aptitude install kubuntu-desktop
```
not ```
sudo kubuntu-desktop
``` ;) Look here: 
[http://www.psychocats.net/ubuntu/kde](http://www.psychocats.net/ubuntu/kde)

Hope this helps!

---

### Post by sasteeleuk on 2006-10-28
Thanks,

This is what happen

shawns@shawns-desktop:~$ sudo aptitude install kubuntu-desktop
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Building tag database... Done      
The following packages are BROKEN:
  ksysguardd 
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
The following packages have unmet dependencies:
  ksysguardd: Depends: libavahi-compat-libdnssd1 (>= 0.6.13) but it is not installable
Resolving dependencies...
The following actions will resolve these dependencies:

Install the following packages:
libavahi-compat-libdnssd1 [0.6.13-2ubuntu2 (edgy, edgy)]

Score is -19

Accept this solution? [Y/n/q/?] Y
The following NEW packages will be automatically installed:
  libavahi-compat-libdnssd1 
The following NEW packages will be installed:
  libavahi-compat-libdnssd1 
0 packages upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/29.6kB of archives. After unpacking 102kB will be used.
Do you want to continue? [Y/n/?] Y
Writing extended state information... Done
(Reading database ... 133820 files and directories currently installed.)
Unpacking libavahi-compat-libdnssd1 (from .../libavahi-compat-libdnssd1_0.6.13-2ubuntu2_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libavahi-compat-libdnssd1_0.6.13-2ubuntu2_i386.deb (--unpack):
 trying to overwrite `/usr/lib/libdns_sd.so.1', which is also in package bonjour
Errors were encountered while processing:
 /var/cache/apt/archives/libavahi-compat-libdnssd1_0.6.13-2ubuntu2_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
dpkg: dependency problems prevent configuration of ksysguardd:
 ksysguardd depends on libavahi-compat-libdnssd1 (>= 0.6.13); however:
  Package libavahi-compat-libdnssd1 is not installed.
dpkg: error processing ksysguardd (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ksysguard:
 ksysguard depends on ksysguardd (= 4:3.5.5-0ubuntu3); however:
  Package ksysguardd is not configured yet.
dpkg: error processing ksysguard (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kubuntu-desktop:
 kubuntu-desktop depends on ksysguard; however:
  Package ksysguard is not configured yet.
dpkg: error processing kubuntu-desktop (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 ksysguardd
 ksysguard
 kubuntu-desktop

 - Should I try to uninstall kubuntu first? If yes, how?

---

### Post by sasteeleuk on 2006-10-28
Problem is sorted. I put my ubuntu CD and it loaded some updates, after rebooting I ran the sudo aptitude update, followed by sudo aptitude install kubuntu-desktop which worked. Thank you.

---

### Post by DoorGunner on 2006-11-02
I am having the same problem.

How do you update with your ubuntu cd??

---

### Post by XVampireX on 2006-11-03
Hey, the problem is in this line:

> 
trying to overwrite `/usr/lib/libdns_sd.so.1', which is also in package bonjour

To fix this:

sudo dpkg -r bonjour

then: sudo aptitude install kubuntu-desktop

enjoy :)

---

### Post by DoorGunner on 2006-11-04
Thank you....

I got it to do it another way totally by accident. 
I had the ubuntu cd in. I gave it the old vulcan neck pinch (cntrl+alt+backspace) and the the cd tried to updadate the package....to make a longstory short.... it fixed itself....

Thank you though.

---

### Post by antler on 2006-11-30
> **XVampireX said:**
> Hey, the problem is in this line:



To fix this:

sudo dpkg -r bonjour

then: sudo aptitude install kubuntu-desktop

enjoy :)

Thankyou so much! Worked like a charm! :-)

---

