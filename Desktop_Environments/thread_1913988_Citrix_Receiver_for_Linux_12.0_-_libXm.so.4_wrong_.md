---
title: "Citrix Receiver for Linux 12.0 - libXm.so.4: wrong ELF class: ELFCLASS64"
date: 2012-01-23
forum: Desktop Environments
---

### Post by Bill Hayes on 2012-01-23
Installed the  64 bit .deb from here:

[http://www.citrix.com/English/ss/downloads/details.asp?downloadId=2316611&productId=1689163](http://www.citrix.com/English/ss/downloads/details.asp?downloadId=2316611&productId=1689163)

Date says 10/5/11 (don't know if that's May 10th or October 5th).

Running:

/opt/Citrix/ICAClient/wfcmgr -icaroot /opt/Citrix/ICAClient

Gives:

/opt/Citrix/ICAClient/wfcmgr: error while loading shared libraries: libXm.so.4: wrong ELF class: ELFCLASS64

I've read:

[https://help.ubuntu.com/community/CitrixICAClientHowTo](https://help.ubuntu.com/community/CitrixICAClientHowTo)

But am none the wiser.

---

### Post by Toz on 2012-01-27
[http://kenfallon.com/to-me-six-months-from-now-how-to-get-citrix-running-on-debian-sid-amd64/]("http://kenfallon.com/to-me-six-months-from-now-how-to-get-citrix-running-on-debian-sid-amd64/").

See the EDIT section half way down. Perhaps the problem is similar?

---

### Post by dmadiedo on 2012-02-13
Taken from:

[http://kenfallon.com/to-me-six-months-from-now-how-to-get-citrix-running-on-debian-sid-amd64/]("http://kenfallon.com/to-me-six-months-from-now-how-to-get-citrix-running-on-debian-sid-amd64/")

After some searching I came across this post which recommended downloading a 32 bit version of libmotif3 for the i386 platform, forcing the install and creating a link from version 3 to version 4.

dpkg -i --force-architecture libmotif*i386.deb
ln -s /usr/lib/libXm.so.3 /usr/lib32/libXm.so.4

maybe this will help you.

---

### Post by TooLboy on 2012-03-20
On Ubuntu Precise Pangolin 12.04 beta 64 bit I had to slightly change the path to use /usr/lib instead of /usr/lib32 for the symlink:


dpkg -i --force-architecture libmotif*i386.deb
ln -s /usr/lib/libXm.so.3 /usr/lib/libXm.so.4

Then it worked.

---

