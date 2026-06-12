---
title: "Just installed kubuntu-dekstop, broken packages [Resolved]"
date: 2007-04-14
forum: Desktop Environments
---

### Post by Peepsalot on 2007-04-14
There is a problem with libavahi-compat-libdnssd1, which it seems both ksysguard and ksysguardd depend on.

I removed the offending packages and tried reinstalling, but still have an error:
[http://www.pastebin.ca/440012](http://www.pastebin.ca/440012)

Does anyone know the issue here?

---

### Post by aysiu on 2007-04-14
```
peeps ~>sudo apt-get install kubuntu-desktop
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  ksysguard ksysguardd libavahi-compat-libdnssd1
The following NEW packages will be installed:
  ksysguard ksysguardd kubuntu-desktop libavahi-compat-libdnssd1
0 upgraded, 4 newly installed, 0 to remove and 4 not upgraded.
Need to get 588kB/618kB of archives.
After unpacking 1925kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Get:1 http://archive.ubuntu.com edgy-updates/main ksysguardd 4:3.5.5-0ubuntu3.4 [76.4kB]
Get:2 http://archive.ubuntu.com edgy-updates/main ksysguard 4:3.5.5-0ubuntu3.4 [498kB]
Get:3 http://archive.ubuntu.com edgy/main kubuntu-desktop 1.22 [14.3kB]
Fetched 588kB in 1s (310kB/s) 
(Reading database ... 234259 files and directories currently installed.)
Unpacking libavahi-compat-libdnssd1 (from .../libavahi-compat-libdnssd1_0.6.13-2ubuntu2.4_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libavahi-compat-libdnssd1_0.6.13-2ubuntu2.4_i386.deb (--unpack):
 trying to overwrite `/usr/lib/libdns_sd.so.1', which is also in package bonjour
Selecting previously deselected package ksysguardd.
Unpacking ksysguardd (from .../ksysguardd_4%3a3.5.5-0ubuntu3.4_i386.deb) ...
Selecting previously deselected package ksysguard.
Unpacking ksysguard (from .../ksysguard_4%3a3.5.5-0ubuntu3.4_i386.deb) ...
Selecting previously deselected package kubuntu-desktop.
Unpacking kubuntu-desktop (from .../kubuntu-desktop_1.22_i386.deb) ...
Errors were encountered while processing:
 /var/cache/apt/archives/libavahi-compat-libdnssd1_0.6.13-2ubuntu2.4_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
``` Try [this](http://www.linuxquestions.org/questions/showthread.php?p=882478#post882478).

---

### Post by Peepsalot on 2007-04-14
I just get the same errors over and over:
```
peeps ~>sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libavahi-compat-libdnssd1
The following NEW packages will be installed:
  libavahi-compat-libdnssd1
0 upgraded, 1 newly installed, 0 to remove and 4 not upgraded.
43 not fully installed or removed.
Need to get 0B/30.0kB of archives.
After unpacking 102kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
(Reading database ... 232964 files and directories currently installed.)
Unpacking libavahi-compat-libdnssd1 (from .../libavahi-compat-libdnssd1_0.6.13-2ubuntu2.4_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libavahi-compat-libdnssd1_0.6.13-2ubuntu2.4_i386.deb (--unpack):
 trying to overwrite `/usr/lib/libdns_sd.so.1', which is also in package bonjour
Errors were encountered while processing:
 /var/cache/apt/archives/libavahi-compat-libdnssd1_0.6.13-2ubuntu2.4_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
peeps ~>sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  ksysguardd: Depends: libavahi-compat-libdnssd1 (>= 0.6.13) but it is not installed
E: Unmet dependencies. Try using -f.
peeps ~>sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libavahi-compat-libdnssd1
The following NEW packages will be installed:
  libavahi-compat-libdnssd1
0 upgraded, 1 newly installed, 0 to remove and 4 not upgraded.
43 not fully installed or removed.
Need to get 0B/30.0kB of archives.
After unpacking 102kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
(Reading database ... 232964 files and directories currently installed.)
Unpacking libavahi-compat-libdnssd1 (from .../libavahi-compat-libdnssd1_0.6.13-2ubuntu2.4_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libavahi-compat-libdnssd1_0.6.13-2ubuntu2.4_i386.deb (--unpack):
 trying to overwrite `/usr/lib/libdns_sd.so.1', which is also in package bonjour
Errors were encountered while processing:
 /var/cache/apt/archives/libavahi-compat-libdnssd1_0.6.13-2ubuntu2.4_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
peeps ~>sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  ksysguardd: Depends: libavahi-compat-libdnssd1 (>= 0.6.13) but it is not installed
E: Unmet dependencies. Try using -f.

```

---

### Post by aysiu on 2007-04-14
Can you try this?

**Step 1**:
[Get a fresh sources.list](http://www.psychocats.net/ubuntu/sources)

**Step 2**: 
Paste this command in the terminal: ```
sudo aptitude update
sudo aptitude install kubuntu-desktop
```

---

### Post by Peepsalot on 2007-04-14
It seems the problem is that I have both bonjour and libavahi... installed.

```
peeps ~>sudo apt-cache search bonjour
libnss-mdns - NSS module for Multicast DNS name resolution
service-discovery-applet - service discovery applet based on avahi for the GNOME panel
libavahi-compat-libdnssd-dev - Development headers for the Avahi Apple Bonjour compatibility library
libavahi-compat-libdnssd1 - Avahi Apple Bonjour compatibility library
bonjour - create an instant network of computers and devices

```

I don't know what these are even for.  I would try to remove bonjour and see if something depends on it, but apt-get just complains about broken packages if I try that.

---

### Post by Peepsalot on 2007-04-14
> **aysiu said:**
> Can you try this?

**Step 1**:
[Get a fresh sources.list](http://www.psychocats.net/ubuntu/sources)

**Step 2**: 
Paste this command in the terminal: ```
sudo aptitude update
sudo aptitude install kubuntu-desktop
```
I just tried this, and still having same problems

---

### Post by Peepsalot on 2007-04-14
Ok i got it working.  Had to do this:
```
sudo apt-get remove ksysguard ksysguardd kubuntu-desktop
sudo apt-get remove bonjour
sudo apt-get install kubuntu-desktop

```

---

