---
title: "[SOLVED] Error with make command"
date: 2008-12-13
forum: General Help
---

### Post by chicothebandit on 2008-12-13
Hi,

I wonder if anyone can help.
Trying to install Broadcom 4320 USB wifi drivers 
and have been folowing this HOW TO:

[http://ubuntuforums.org/showthread.php?t=847226](http://ubuntuforums.org/showthread.php?t=847226)

I get to the point when I need to build the new drivers but I just get errors when running make command as follows.


Code:

[I]charlie@sheen:/bcm4320drivers$ ls
rndis_wlan  rndis_wlan-snapshot-20080509.tar.gz

charlie@sheen:/bcm4320drivers$ cd rndis_wlan 

charlie@sheen:/bcm4320drivers/rndis_wlan$ ls
cdc_ether.c  clean.sh  Makefile  rndis_host.c  
rndis_wlan.c  usbnet.h cdc.h Kbuild    README    
rndis_host.h  usbnet.c

charlie@sheen:/bcm4320drivers/rndis_wlan$ sudo make
make -C /lib/modules/2.6.24-21-server/build 
SUBDIRS=/bcm4320drivers/rndis_wlan modules
make: *** /lib/modules/2.6.24-21-server/build: No 
such file or directory.  Stop.
make: *** [default] Error 2

[/I]

I tried creating the folder called /lib/modules/2.6.24-21-server/build

and running the make command again but just get another error

Code:
[I]charlie@sheen:~/bcm4320drivers/rndis_wlan$ sudo make
make -C /lib/modules/2.6.24-21-server/build SUBDIRS=/home/charlie/bcm4320drivers/rndis_wlan modules
make[1]: Entering directory `/lib/modules/2.6.24-21-server/build'
make[1]: *** No rule to make target `modules'.  Stop.
make[1]: Leaving directory `/lib/modules/2.6.24-21-server/build'
make: *** [default] Error 2

[/I]

I think I may have some modules are packages missing.

Any suggestions???

Thanks

---

### Post by PmDematagoda on 2008-12-13
From the error message, you seem to be missing the kernel source. Did you install the kernel source?

---

### Post by chicothebandit on 2008-12-13
Hi,

Thanks for the reply.

/usr/src/linux doesn't show anything so I'm assuming the kernel source is missing.

Code:

[I]charlie@sheen:/bcm4320drivers/rndis_wlan$ cd /usr/src/linux
bash: cd: /usr/src/linux: No such file or directory
charlie@sheen:/bcm4320drivers/rndis_wlan$ cd /usr/src
charlie@sheen:/usr/src$ ls
linux-headers-2.6.24-16          linux-headers-2.6.24-18-generic
linux-headers-2.6.24-16-generic  linux-headers-2.6.24-19
linux-headers-2.6.24-17          linux-headers-2.6.24-19-generic
linux-headers-2.6.24-17-generic  linux-headers-2.6.24-21
linux-headers-2.6.24-18          linux-headers-2.6.24-21-generic
charlie@sheen:/usr/src$ 

charlie@sheen:/usr/src$ uname -r
2.6.24-21-server
[/I]

Do I have to add kernel source linux-2.6.24-21 to /usr/src and then create new symbolic link ln -s linux-2.6.24-21 linux ?

Thanks,

---

### Post by PmDematagoda on 2008-12-14
Try installing the linux-kernel-devel package and see if you can continue then.

---

### Post by chicothebandit on 2008-12-14
Hello,

Thank you very much for you help PmDematagoda. 

That worked and I have now managed to install driver without error. System appears to be recognising the device ok now as syslog reports the following.

*NetworkManager: <info> wlan0: Device is fully-supported using driver 'rndis_wlan'.* :)

Just need to configure network settings now!

Cheers

---

### Post by PmDematagoda on 2008-12-14
> **chicothebandit said:**
> Hello,

Thank you very much for you help PmDematagoda. 

That worked and I have now managed to install driver without error. System appears to be recognising the device ok now as syslog reports the following.

*NetworkManager: <info> wlan0: Device is fully-supported using driver 'rndis_wlan'.* :)

Just need to configure network settings now!

Cheers
Glad to hear it worked out:).

---

