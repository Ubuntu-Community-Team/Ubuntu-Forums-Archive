---
title: "E: Sub-process /usr/bin/dpkg returned an error code (1)"
date: 2008-12-12
forum: Desktop Environments
---

### Post by StaSiS on 2008-12-12
Anytime I try to install anything with apt-get I get this error at the end, I have searched a bit and found many causes such as no disk space etc but nothing has fixed it, most installed apps seem to work fine though.

Error were encountered while processing:
 system-tools-backends
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by StaSiS on 2008-12-12
anyone?

---

### Post by neu2buntu on 2008-12-12
hi...this happened to me ages ago .. i googled a bit for you and im almost sure this command sorted it out      sudo dpkg --configure -a         .

---

### Post by StaSiS on 2008-12-13
> **chrissy.mc.1@hotmail.co.u said:**
> hi...this happened to me ages ago .. i googled a bit for you and im almost sure this command sorted it out      sudo dpkg --configure -a         .

Tried that, get a similar error when I try that command:

Setting up system-tools-backends (2.6.0-1ubuntu1.1) ...
 * Starting System Tools Backends system-tools-backends                         invoke-rc.d: initscript system-tools-backends, action "start" failed.
dpkg: error processing system-tools-backends (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 system-tools-backends

---

### Post by phyz on 2008-12-13
i'm also having that kind of problem too....

```
phyz@myphynix:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libboost-thread1.34.1 libboost-date-time1.34.1 deluge-torrent-common
  libboost-filesystem1.34.1
The following packages will be REMOVED:
  deluge-torrent-common libboost-date-time1.34.1 libboost-filesystem1.34.1
  libboost-thread1.34.1
0 upgraded, 0 newly installed, 4 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 7078kB disk space will be freed.
Do you want to continue [Y/n]? y
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
(Reading database ... 108522 files and directories currently installed.)
Removing deluge-torrent-common ...
Removing libboost-date-time1.34.1 ...
Removing libboost-filesystem1.34.1 ...
Removing libboost-thread1.34.1 ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Setting up msttcorefonts (2.5) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing msttcorefonts (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 msttcorefonts
E: Sub-process /usr/bin/dpkg returned an error code (1)
phyz@myphynix:~$ 

```


is there any solutions?

---

### Post by w31mrk on 2009-01-18
Hi,
Does anyone have any ideas about this... Its getting a little anoying

---

### Post by drtvasudevan on 2009-05-06
> **w31mrk said:**
> Hi,
Does anyone have any ideas about this... Its getting a little anoying

me too! annoyed.

---

### Post by kelean on 2009-05-17
> **StaSiS said:**
> Anytime I try to install anything with apt-get I get this error at the end, I have searched a bit and found many causes such as no disk space etc but nothing has fixed it, most installed apps seem to work fine though.

Error were encountered while processing:
 system-tools-backends
E: Sub-process /usr/bin/dpkg returned an error code (1)

I had this same problem and searched a long time and found nothing.  Then I happen to be reading a post that had nothing to do with the problem for the answer.

What you need to do is this.
1. from the command line stop system-tools-backends.
2. Then run sudo dpkg --configure -a

It has something to do with the backend tools running and it cannot reconfigure with it running.  I dont know if it was a bug oor not.  I tried to find the post but could not.

I hope this helps, Kelean.

---

### Post by IzByFl on 2010-07-07
[http://www.linuxquestions.org/questions/debian-26/sub-process-usr-bin-dpkg-returned-an-error-code-1-a-171107/](http://www.linuxquestions.org/questions/debian-26/sub-process-usr-bin-dpkg-returned-an-error-code-1-a-171107/)

post #6 worked for me

---

### Post by bobwdn on 2010-09-15
post #6 worked for me at [http://www.linuxquestions.org/questions/debian-26/sub-process-usr-bin-dpkg-returned-an-error-code-1-a-171107/worked](http://www.linuxquestions.org/questions/debian-26/sub-process-usr-bin-dpkg-returned-an-error-code-1-a-171107/worked) for me, too.

Thanks!!!

---

