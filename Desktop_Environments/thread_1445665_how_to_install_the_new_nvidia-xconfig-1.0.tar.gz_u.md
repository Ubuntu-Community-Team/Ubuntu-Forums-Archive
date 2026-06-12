---
title: "how to install the new nvidia-xconfig-1.0.tar.gz utility"
date: 2010-04-02
forum: Desktop Environments
---

### Post by danmarius1981 on 2010-04-02
Hello everybody,
 

 Nvidia now provides a utility to easy configure the X server configuration file (besides the manual configuration). It is provided as a tar.gz file and it can be downloaded from here:
 

 [http://www.nvidia.com/object/linux_display_ia32_96.43.16.html](http://www.nvidia.com/object/linux_display_ia32_96.43.16.html)
 

 I used the standard procedure to install such files:
 

 

 unpack the archive
 change directory as root into the unpacked archive
 ./configure
 make
 make install
 

 but it did not work. After the ./configure command it says that it cannot find scuh file or directory. 

 

 I am using Ubuntu 9.10. My video card is GeForce 4 MX and the driver is 96.43.13.  
 The archive does not provide any install instructions.  
 

 Guys, any help would be highly appreciated!

---

### Post by byStanderone on 2010-04-02
...the safe way in installing apps/drivers is thru synaptic, dependencies provided automatically. also...under system>administration, you could have installed the nvidia driver by clicking hardaware drivers...

---

