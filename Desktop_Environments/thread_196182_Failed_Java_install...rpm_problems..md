---
title: "Failed Java install...rpm problems."
date: 2006-06-13
forum: Desktop Environments
---

### Post by jbavousett on 2006-06-13
I got the following when I ukpacked the RPM:

> Do you agree to the above license terms? [yes or no]
yes
Unpacking...
Checksumming...
0
0
Extracting...
UnZipSFX 5.42 of 14 January 2001, by Info-ZIP (Zip-Bugs@lists.wku.edu).
  inflating: jre-1_5_0_07-linux-i586.rpm
./jre-1_5_0_07-linux-i586-rpm.bin: line 648: rpm: command not found

Done.
root@dimension2400:/usr/java# 

Then I get this when I try and run the RPM...

> root@dimension2400:/usr/java# ls
jre-1_5_0_07-linux-i586.rpm  jre-1_5_0_07-linux-i586-rpm.bin
root@dimension2400:/usr/java# rpm -iv jre-1_5_0_07-linux-i586.rpm
bash: rpm: command not found
root@dimension2400:/usr/java# 

Anyone know what I'm messing up?

---

### Post by mlind on 2006-06-13
You should not be using rpm's with Debian based distro, like Ubuntu is. Prefer only
.deb packages, which are somwhat equivalent of .rpm packages.

With .deb packages, you play with aptitude/apt-get or dpkg, not rpm.

Instructions for installing Java, see [https://wiki.ubuntu.com/Java](https://wiki.ubuntu.com/Java)

---

