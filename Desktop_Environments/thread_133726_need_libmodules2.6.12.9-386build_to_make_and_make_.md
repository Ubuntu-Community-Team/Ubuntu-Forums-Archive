---
title: "need /lib/modules/2.6.12.9-386/build to make and make intall?"
date: 2006-02-20
forum: Desktop Environments
---

### Post by dcast on 2006-02-20
Hi im trying to install a driver that came in tar.gz format and I followed the readme in it and when I get to "make" the terminal spits out\


david@ubuntu:~/zd1211-4715/zdsta$ make
/lib/modules/2.6.12-9-386/build
/home/david/zd1211-4715/zdsta
-I/home/david/zd1211-4715/zdsta/src/include -fomit-frame-pointer -O -Wall -Wstrict-prototypes -pipe -DHOST_IF_USB -DAMAC -DGCCK -DOFDM -DUSE_EP4_SET_REG -DDOWNLOADFIRMWARE -DfTX_GAIN_OFDM=0 -DfNEW_CODE_MAP=1 -DfWRITE_WORD_REG=1 -DfREAD_MUL_REG=1
make -C /lib/modules/2.6.12-9-386/build SUBDIRS=/home/david/zd1211-4715/zdsta modules
make: *** /lib/modules/2.6.12-9-386/build: No such file or directory.  Stop.
make: *** [all] Error 2



then I tried to simply create teh folder with mkdir and then tried make again and this time I got:



david@ubuntu:~/zd1211-4715/zdsta$ make
/lib/modules/2.6.12-9-386/build
/home/david/zd1211-4715/zdsta
-I/home/david/zd1211-4715/zdsta/src/include -fomit-frame-pointer -O -Wall -Wstrict-prototypes -pipe -DHOST_IF_USB -DAMAC -DGCCK -DOFDM -DUSE_EP4_SET_REG -DDOWNLOADFIRMWARE -DfTX_GAIN_OFDM=0 -DfNEW_CODE_MAP=1 -DfWRITE_WORD_REG=1 -DfREAD_MUL_REG=1
make -C /lib/modules/2.6.12-9-386/build SUBDIRS=/home/david/zd1211-4715/zdsta modules
make[1]: Entering directory `/lib/modules/2.6.12-9-386/build'
make[1]: *** No rule to make target `modules'.  Stop.
make[1]: Leaving directory `/lib/modules/2.6.12-9-386/build'
make: *** [all] Error 2
david@ubuntu:~/zd1211-4715/zdsta$




what does that mean? should I copy the modules from teh driver into thefolder or something? any help is appreciated.

---

### Post by Ramses de Norre on 2006-02-20
```
sudo apt-get install linux-headers-'uname -r' build-essential
```
Think you haven't installed one of those two.

---

### Post by dcast on 2006-02-20
build essential was installed, I installed linux-headers for my kernel, unfortunately still the same problem. any other ideas?

---

### Post by hajk on 2006-02-21
Command "export CC=gcc-3.4", then "make clean" before you compile again.

---

### Post by dcast on 2006-02-21
nope, no luck thanks anyway. I installed a driver I found on the net and it was a .deb. Hal device manager now sees it as a wireless adapter wlan0 but when I try "iwconfig wlan0" it tells me there is no such device. Can I make the driver be used on the adapter? or something like that? Also when I leave the adapter plugged in it hangs on "starting hotplug subsystem" during boot. Why is that?

---

### Post by hajk on 2006-02-21
The deb-package you found was probably compiled for another kernel version, or with the wrong version of GCC. Both must match the installed kernel, the one that shows when issuing the command "uname -r".

---

### Post by dcast on 2006-02-21
I got the driver from here. [http://dir.filewatcher.com/d/Debian/all/base/zd1211-source_0.0.0.svnr23-3_all.deb.176918.html](http://dir.filewatcher.com/d/Debian/all/base/zd1211-source_0.0.0.svnr23-3_all.deb.176918.html) Also when I use iwconfig wlan0 it now just tells me there are no wireless extensions. Is this progress? how do i know if it for the wrong kernel? it says nothing about kernel versions on the above site. Thanks for your help.

---

