---
title: "NetGear Driver dosnt compail"
date: 2006-06-17
forum: Desktop Environments
---

### Post by SwaroopKunduru on 2006-06-17
Hi All,

I am trying to compile netgear driver I got the exception below.

make -C /lib/modules/2.6.15-23-386/build SUBDIRS=/home/swaroop/.install_SW/rtl8180-0.21 MODVERDIR=/home/swaroop/.install_SW/rtl8180-0.21 modules
make: *** /lib/modules/2.6.15-23-386/build: No such file or directory.  Stop.
make: *** [modules] Error 2


when I type ls -altr /lib/modules/2.6.15-23-386/build  I got this.

ls: /lib/modules/2.6.15-23-386/build: No such file or directory

How to deal with this.

Please help. Why I dont have build folder in  /lib/modules/2.6.15-23-386.

Regards,

Swaroop Kunduru.

---

### Post by SwaroopKunduru on 2006-06-18
Hi All,

After some help from the forum I had moved little further. I am getting this.

make -C /lib/modules/2.6.15-25-386/build SUBDIRS=/home/swaroop/.install_SW/rtl8180-0.21 MODVERDIR=/home/swaroop/.install_SW/rtl8180-0.21 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.15-25-386'
CC [M] /home/swaroop/.install_SW/rtl8180-0.21/ieee80211_rx.o
CC [M] /home/swaroop/.install_SW/rtl8180-0.21/ieee80211_tx.o
CC [M] /home/swaroop/.install_SW/rtl8180-0.21/ieee80211_wx.o
CC [M] /home/swaroop/.install_SW/rtl8180-0.21/ieee80211_module.o
CC [M] /home/swaroop/.install_SW/rtl8180-0.21/ieee80211_crypt.o
CC [M] /home/swaroop/.install_SW/rtl8180-0.21/ieee80211_crypt_wep.o
/home/swaroop/.install_SW/rtl8180-0.21/ieee80211_crypt_wep.c:27:2: warning: #warning CONFIG_CRYPTO_ARC4 is required to build this module.
CC [M] /home/swaroop/.install_SW/rtl8180-0.21/r8180_core.o
/home/swaroop/.install_SW/rtl8180-0.21/r8180_core.c: In function ‘rtl8180_pci_probe’:
/home/swaroop/.install_SW/rtl8180-0.21/r8180_core.c:3632: error: ‘struct pci_dev’ has no member named ‘slot_name’
make[2]: *** [/home/swaroop/.install_SW/rtl8180-0.21/r8180_core.o] Error 1
make[1]: *** [_module_/home/swaroop/.install_SW/rtl8180-0.21] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.15-25-386'
make: *** [2.6] Error 2

What should I do? Please help Help Help ...................

Regards,

---

