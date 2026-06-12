---
title: "How to install network drivers in Dell Inspiron 5420 with ubuntu 10.04?"
date: 2013-01-26
forum: Dell Ubuntu Support (CLOSED)
---

### Post by cybersa on 2013-01-26
I tried this method to install 
[http://askubuntu.com/questions/233575/how-to-install-network-drivers-in-dell-inspiron-5420](http://askubuntu.com/questions/233575/how-to-install-network-drivers-in-dell-inspiron-5420)
But it show me a error:
```
$sudo make 
make -C /lib/modules/2.6.32-38-generic/build M=/home/cyberboy/Desktop/compat-wireless-2012-07-03-p modules 
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-38-generic' 
scripts/Makefile.build:44: /home/cyberboy/Desktop/compat-wireless-2012-07-03-p/drivers/net/ethernet/atheros/alx/Makefile: No such file or directory 
make[4]: *** No rule to make target `/home/cyberboy/Desktop/compat-wireless-2012-07-03-p/drivers/net/ethernet/atheros/alx/Makefile'.  Stop. 
make[3]: *** [/home/cyberboy/Desktop/compat-wireless-2012-07-03-p/drivers/net/ethernet/atheros/alx] Error 2 
make[2]: *** [/home/cyberboy/Desktop/compat-wireless-2012-07-03-p/drivers/net/ethernet/atheros] Error 2 
make[1]: *** [_module_/home/cyberboy/Desktop/compat-wireless-2012-07-03-p] Error 2 make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-38-generic' make: *** [modules] Error 2
```I'm using Ubuntu 64bit 10.04

---

