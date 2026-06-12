---
title: "I can't use my Update Manager on ubuntu 8.10"
date: 2009-04-18
forum: General Help
---

### Post by g35celicaz on 2009-04-18
I just installed ubuntu 8.10 on my laptop yesterday. Once I finished installing it, I did 291 updates using the update manager.

When it finished installing I went to this web site:
[http://linuxowns.wordpress.com/2008/10/30/5-things-to-do-after-installing-ubuntu-810-intrepid-ibex/](http://linuxowns.wordpress.com/2008/10/30/5-things-to-do-after-installing-ubuntu-810-intrepid-ibex/)

This web site shows you 5 things to do after installing ubuntu 8.10

The first thing it said to do is to install this:dvd support, audio and video codecs, flash and java

So I installed it by coping and pasting this command in the terminal window:

sudo wget [http://www.medibuntu.org/sources.list.d/intrepid.list](http://www.medibuntu.org/sources.list.d/intrepid.list) -O /etc/apt/sources.list.d/medibuntu.list && wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add - && sudo apt-get update && sudo apt-get install -y ubuntu-restricted-extras non-free-codecs w32codecs totem-mozilla libdvdcss2

It installed successfully 


The second thing it said to install was this:rar and 7z  support

So I put this command in the terminal window:

sudo apt-get install p7zip-full

Unfortunately it did not work 

It gave me this:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 


After this problem the update manager said that there was 1 update available. So I pressed install and then it gave me this:

An error occurred

The following details are provided:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.


Please Help

 - Thanks

---

### Post by drs305 on 2009-04-18
You must run the command as root to clear the error:
```
sudo dpkg --configure -a
```

Welcome to the ubuntu forums.

---

