---
title: "Conexant Modem on Kubuntu Kernel 2.6.15.23"
date: 2006-09-02
forum: Desktop Environments
---

### Post by nitin_india on 2006-09-02
Hello,
This is my first post on the forum. I have tried to look for Howto procedure for installing Conexant HSF modem. I am using Kubuntu 6.06 LTS with Kernel version 2.6.15.23
I have downloaded the free driver from Linuxant and works fine with the modem and with KPPP. However the speed is limited to 14.4 Kbps. I need to know if there is any pacakge or process to install a free driver for the modem.

I am a new user to Linux and is looking for support here.
Thanks in advance.
Nitin Deo

---

### Post by williamts99 on 2006-09-13
Try this link [http://ubuntuforums.org/showthread.php?t=190728&highlight=Conexant+HSF](http://ubuntuforums.org/showthread.php?t=190728&highlight=Conexant+HSF)


> **nitin_india said:**
> Hello,
This is my first post on the forum. I have tried to look for Howto procedure for installing Conexant HSF modem. I am using Kubuntu 6.06 LTS with Kernel version 2.6.15.23
I have downloaded the free driver from Linuxant and works fine with the modem and with KPPP. However the speed is limited to 14.4 Kbps. I need to know if there is any pacakge or process to install a free driver for the modem.

I am a new user to Linux and is looking for support here.
Thanks in advance.
Nitin Deo

---

### Post by nitin_india on 2006-09-18
I have visited the link however the link [https://wiki.ubuntu.com/DialupModemH...hsfpci.tar.bz2](https://wiki.ubuntu.com/DialupModemH...hsfpci.tar.bz2) seems to be broken. Whenever I try to extract the file I get an error.

Nitin Deo

---

### Post by williamts99 on 2006-09-20
Well, I have a copy of it here. [http://ubuntuconexant.williamts99.com/](http://ubuntuconexant.williamts99.com/)

[http://ubuntuconexant.williamts99.com/modem-hsfpci.tar.bz2](http://ubuntuconexant.williamts99.com/modem-hsfpci.tar.bz2)

---

### Post by nitin_india on 2006-09-22
Hello,

Thanks for the link, I could download all the required files. However I do not have lot of deb pacakges loaded into my desktop. Even I could not run the make command. Now I have located all of the .deb packages in the install CD. However I would need to load these for the modem to work.
I have few questions.

How come none of these are installed. I have installed Kubuntu from the Kubuntu Live CD.
Can I or Do I need to install all of them.
How easily I can add path of the CD for the apt-get command to work for the packages to work from CD.
Thanks for the help in advance.

---

### Post by nitin_india on 2006-09-26
Here is the update for all the efforts that have not yielded any good results.

Firstly I tried with Method A as per the link above and did got the following:

root@deo-desktop:/home/deo/Desktop/HSFmodem# 

root@deo-desktop:/home/deo/Desktop/conexant#


root@deo-desktop:/home/deo/Desktop/HSFmodem# ./HOWTO.txt

please apt-get install debhelper from the installation CD
root@deo-desktop:/home/deo/Desktop/HSFmodem# apt-get install debhelper
Reading package lists... Done
Building dependency tree... Done
Package debhelper is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package debhelper has no installation candidate
root@deo-desktop:/home/deo/Desktop/HSFmodem# apt-get install fakeroot
Reading package lists... Done
Building dependency tree... Done
fakeroot is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
root@deo-desktop:/home/deo/Desktop/HSFmodem# apt-get debhelper
E: Invalid operation debhelper
root@deo-desktop:/home/deo/Desktop/HSFmodem# apt-get install debhelper
Reading package lists... Done
Building dependency tree... Done
Package debhelper is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package debhelper has no installation candidate
root@deo-desktop:/home/deo/Desktop/HSFmodem# apt-get install build-essential
Reading package lists... Done
Building dependency tree... Done
build-essential is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
root@deo-desktop:/home/deo/Desktop/HSFmodem# apt-get install linux-headers-`unam
e -r`
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  linux-headers-2.6.15-23
The following NEW packages will be installed:
  linux-headers-2.6.15-23 linux-headers-2.6.15-23-386
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/7747kB of archives.
After unpacking 79.5MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Selecting previously deselected package linux-headers-2.6.15-23.
(Reading database ... 69073 files and directories currently installed.)
Unpacking linux-headers-2.6.15-23 (from .../linux-headers-2.6.15-23_2.6.15-23.39                                                              _i386.deb) ...
Selecting previously deselected package linux-headers-2.6.15-23-386.
Unpacking linux-headers-2.6.15-23-386 (from .../linux-headers-2.6.15-23-386_2.6.                                                              15-23.39_i386.deb) ...
Setting up linux-headers-2.6.15-23 (2.6.15-23.39) ...

Setting up linux-headers-2.6.15-23-386 (2.6.15-23.39) ...

Where can I get the dbhelper package. I have already addedd the CDrom as reposetory destination.

When I tried with method B I get the following results.

root@deo-desktop:/home/deo/Desktop/conexant# make
make -C inf
make[1]: Entering directory `/home/deo/Desktop/conexant/inf'
cc -I../modules/imported/include -I../modules/osspec/include -O2 -Wall   -c -o inf2bin.o inf2bin.c
inf2bin.c: In function &#8216;ProcessString&#8217;:
inf2bin.c:236: warning: pointer targets in assignment differ in signedness
inf2bin.c: In function &#8216;ProcessCtryStruct&#8217;:
inf2bin.c:393: warning: pointer targets in assignment differ in signedness
cc -o hsfinf2bin inf2bin.o
(./preprocess.sh linux_hsfi-14f1-2f00.bin > linux_hsfi-14f1-2f00.bin.temp; ./hsfinf2bin linux_hsfi-14f1-2f00.bin.temp linux_hsfi-14f1-2f00.bin)
(./preprocess.sh linux_hsfi-8086-24c6.bin > linux_hsfi-8086-24c6.bin.temp; ./hsfinf2bin linux_hsfi-8086-24c6.bin.temp linux_hsfi-8086-24c6.bin)
(./preprocess.sh linux_hsfi-14f1-2f30.bin > linux_hsfi-14f1-2f30.bin.temp; ./hsfinf2bin linux_hsfi-14f1-2f30.bin.temp linux_hsfi-14f1-2f30.bin)
make[1]: Leaving directory `/home/deo/Desktop/conexant/inf'
make -C modules
make[1]: Entering directory `/home/deo/Desktop/conexant/modules'
make -C /lib/modules/$(uname -r)/build M=/home/deo/Desktop/conexant/modules modules
make[2]: Entering directory `/lib/modules/2.6.15-23-386/build'
make[2]: *** No rule to make target `modules'.  Stop.
make[2]: Leaving directory `/lib/modules/2.6.15-23-386/build'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/home/deo/Desktop/conexant/modules'
make: *** [all] Error 2

Please suggest any further action on this.

Thanks

Nitin

---

### Post by philAtoulouse on 2007-01-10
Hi,
Could you finally find a solution?

---

### Post by nitin_india on 2007-01-13
NO, Still waiting for Miracle to happen.

---

