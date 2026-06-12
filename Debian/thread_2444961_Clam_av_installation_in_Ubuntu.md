---
title: "Clam av installation in Ubuntu"
date: 2020-06-07
forum: Debian
---

### Post by rajeshprabha10 on 2020-06-07
I am trying to install clam av in Debian(running as container) but couldnt install it as I am having "unable to locate package error".


root@ff3a52f90f58:~# apt-get install clam-daemon
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Unable to locate package clam-daemon
root@ff3a52f90f58:~# apt-get install clam-av
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Unable to locate package clam-av


have attached /etc/apt/source.list.


had added " deb-src [http://deb.debian.org/debian](http://deb.debian.org/debian) stretch main " in etc/apt/source.list and did apt-get update, didnt work out


Any suggestion or helpis highly appreciated
[COLOR=#FFFFFF][FONT=monospace]

[/FONT][/COLOR]

---

### Post by wildmanne39 on 2020-06-07
*Thread moved to **Debian for a more appropriate fit**.*

---

### Post by deadflowr on 2020-06-07
It's clamav.
Not clam-av.
[https://wiki.debian.org/ClamAV]("https://wiki.debian.org/ClamAV")

---

### Post by SeijiSensei on 2020-06-07
Nor is the package for clamd called clam-daemon, but "clamav-daemon."  Take a moment to acquaint yourself with the useful command apt-cache."  Here is a search for packages whose name or description includes "clamav".
```
apt-cache search clamav
```

The basic packages appear at the top of the list:
```

clamav - anti-virus utility for Unix - command-line interface
clamav-base - anti-virus utility for Unix - base package
clamav-daemon - anti-virus utility for Unix - scanner daemon
clamav-docs - anti-virus utility for Unix - documentation
clamav-freshclam - anti-virus utility for Unix - virus database update utility
clamdscan - anti-virus utility for Unix - scanner client

```
Some of these are "dependencies."  Installing clamav automatically installs clamav-base and clamav-freshclam. Installing "clamav-daemon" brings along those and clamdscan as well.  There are also a couple of libraries in the list.

BTW, if you're installing ClamAV to fight viruses on a Linux distribution, it's not worth it because your system is **much** less vulnerable than one running Windows.   However, if you have Windows files on this machine, like a Windows partition for dual-booting, or directories you're sharing with Windows machines, ClamAV is a worthwhile investment.

Clamd runs full-time on my email servers so I can scan incoming mail for dirty attachments with [MailScanner]("https://www.mailscanner.info/"), but I never bother with it in all-Linux environments like my home network.

---

