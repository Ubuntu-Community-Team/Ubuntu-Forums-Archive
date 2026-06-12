---
title: "AMD64 not remapping table"
date: 2005-07-24
forum: Desktop Environments
---

### Post by harrisxml on 2005-07-24
I'm trying to install J2RE for AMD64...  Here are the commands that get me to this point:

$ sudo apt-get install java-package fakeroot
$ fakeroot make-jpkg jre-1_5_0-linux-amd64.bin
$ sudo dpkg -i sun-j2re1.5_1.5.0+update00_amd64.deb   #Problem Ocurrs Here

After entering the last line I get:

```
harrisxml@harrisxml:~$ sudo dpkg -i sun-j2re1.5_1.5.0+update00_amd64.deb
(Reading database ... 64209 files and directories currently installed.)
Preparing to replace sun-j2re1.5 1.5.0+update00 (using sun-j2re1.5_1.5.0+update00_amd64.deb) ...
Unpacking replacement sun-j2re1.5 ...
Setting up sun-j2re1.5 (1.5.0+update00) ...
dpkg: warning, architecture `amd64' not in remapping table
``` 

What's up with this?

---

