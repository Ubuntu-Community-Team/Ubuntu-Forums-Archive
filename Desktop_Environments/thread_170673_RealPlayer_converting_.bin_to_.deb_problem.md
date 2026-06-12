---
title: "RealPlayer converting .bin to .deb problem"
date: 2006-05-05
forum: Desktop Environments
---

### Post by marcfell27 on 2006-05-05
I'm trying to install Realplayer. I downloaded as a bin file.

Used the following to convert .bin to .deb :
*********************************************************
marcus@ubuntu:~/EXE$ chmod +x RealPlayer10GOLD.bin
marcus@ubuntu:~/EXE$ fakeroot make-jpkg RealPlayer10GOLD.bin
Creating temporary directory: /tmp/make-jpkg.XXXXA20NOt
Loading plugins: blackdown-j2re.sh blackdown-j2sdk.sh common.sh ibm-j2re.sh ibm-j2sdk.sh j2re.sh j2sdk-doc.sh j2sdk.sh j2se.sh sun-j2re.sh sun-j2sdk-doc.sh sun-j2sdk.sh
sh: gcc: command not found
dpkg-architecture: warning: Couldn't determine gcc system type, falling back to default (native compilation)
sh: gcc: command not found
dpkg-architecture: warning: Couldn't determine gcc system type, falling back to default (native compilation)
sh: gcc: command not found
dpkg-architecture: warning: Couldn't determine gcc system type, falling back to default (native compilation)
sh: gcc: command not found
dpkg-architecture: warning: Couldn't determine gcc system type, falling back to default (native compilation)
sh: gcc: command not found
dpkg-architecture: warning: Couldn't determine gcc system type, falling back to default (native compilation)
sh: gcc: command not found
dpkg-architecture: warning: Couldn't determine gcc system type, falling back to default (native compilation)
sh: gcc: command not found
dpkg-architecture: warning: Couldn't determine gcc system type, falling back to default (native compilation)

No matching plugin was found.
Removing temporary directory: done
marcus@ubuntu:~/EXE$ sudo apt-get install fakeroot
Reading package lists... Done
Building dependency tree... Done
fakeroot is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
marcus@ubuntu:~/EXE$ fakeroot make-jpkg RealPlayer10GOLD.bin
Creating temporary directory: /tmp/make-jpkg.XXXXxXXOGC
Loading plugins: blackdown-j2re.sh blackdown-j2sdk.sh common.sh ibm-j2re.sh ibm-j2sdk.sh j2re.sh j2sdk-doc.sh j2sdk.sh j2se.sh sun-j2re.sh sun-j2sdk-doc.sh sun-j2sdk.sh
sh: gcc: command not found
dpkg-architecture: warning: Couldn't determine gcc system type, falling back to default (native compilation)
sh: gcc: command not found
dpkg-architecture: warning: Couldn't determine gcc system type, falling back to default (native compilation)
sh: gcc: command not found
dpkg-architecture: warning: Couldn't determine gcc system type, falling back to default (native compilation)
sh: gcc: command not found
dpkg-architecture: warning: Couldn't determine gcc system type, falling back to default (native compilation)
sh: gcc: command not found
dpkg-architecture: warning: Couldn't determine gcc system type, falling back to default (native compilation)
sh: gcc: command not found
dpkg-architecture: warning: Couldn't determine gcc system type, falling back to default (native compilation)
sh: gcc: command not found
dpkg-architecture: warning: Couldn't determine gcc system type, falling back to default (native compilation)

No matching plugin was found.
Removing temporary directory: done
*************************************************************************
Please help, I just wanna play mp3's on my ubuntu 5.10 before I go completely bald...

Cheers

---

### Post by nanotube on 2006-05-05
hmm well, it looks like you are missing gcc. 
run this:
```
sudo apt-get install build-essential
```
that will install gcc, as well as some other software build tools.
then try your thing again.

---

