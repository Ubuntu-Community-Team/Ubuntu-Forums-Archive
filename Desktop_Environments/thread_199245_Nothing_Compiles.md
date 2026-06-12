---
title: "Nothing Compiles"
date: 2006-06-18
forum: Desktop Environments
---

### Post by SwaroopKunduru on 2006-06-18
Hi All,

When I am trying to compile ndiswrapper.8 I am getting this. 

Can't find kernel sources in /lib/modules/2.6.15-25-386/build;
  give the path to kernel sources with KSRC=<path>             argument to make
make[1]: *** [prereq_check] Error 1
make[1]: Leaving directory `/home/swaroop/.install_SW/ndiswrapper-1.8/driver'
make: *** [all] Error 2

Did I miss any thing before compiling?

Regards,

Swaroop Kunduru.

---

### Post by joelito on 2006-06-18
install the kernel sources. I think the command is
```
sudo apt-get install linux-source
```

---

### Post by SwaroopKunduru on 2006-06-18
I did the same but it is the same, nothing worked out. I did not see a build folder in /lib/modules/2.6.15-23-386/

Regards,

Swaroop Kunduru.

---

### Post by Ramses de Norre on 2006-06-18
Try with ```
sudo aptitude install linux-headers-`uname -r` kernel-headers-`uname -r`
```

---

### Post by SwaroopKunduru on 2006-06-18
I am trying to compile drivers the scripts are looking for .config file in the build folder in  /lib/modules/2.6.15-23-386/  but there is no build folder in that directory. I tried both of the above commands I did not see the folder still and it is the same.

Regards,

Swaroop Kunduru.

---

### Post by SwaroopKunduru on 2006-06-18
Something worked this time I see a build link insted of folder. But I have another problem it is asking this. 

make -C /lib/modules/2.6.15-25-386/build SUBDIRS=/home/swaroop/.install_SW/rtl8180-0.21 MODVERDIR=/home/swaroop/.install_SW/rtl8180-0.21 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.15-25-386'
  CC [M]  /home/swaroop/.install_SW/rtl8180-0.21/ieee80211_rx.o
  CC [M]  /home/swaroop/.install_SW/rtl8180-0.21/ieee80211_tx.o
  CC [M]  /home/swaroop/.install_SW/rtl8180-0.21/ieee80211_wx.o
  CC [M]  /home/swaroop/.install_SW/rtl8180-0.21/ieee80211_module.o
  CC [M]  /home/swaroop/.install_SW/rtl8180-0.21/ieee80211_crypt.o
  CC [M]  /home/swaroop/.install_SW/rtl8180-0.21/ieee80211_crypt_wep.o
/home/swaroop/.install_SW/rtl8180-0.21/ieee80211_crypt_wep.c:27:2: warning: #warning CONFIG_CRYPTO_ARC4 is required to build this module.
  CC [M]  /home/swaroop/.install_SW/rtl8180-0.21/r8180_core.o
/home/swaroop/.install_SW/rtl8180-0.21/r8180_core.c: In function ‘rtl8180_pci_probe’:
/home/swaroop/.install_SW/rtl8180-0.21/r8180_core.c:3632: error: ‘struct pci_dev’ has no member named ‘slot_name’
make[2]: *** [/home/swaroop/.install_SW/rtl8180-0.21/r8180_core.o] Error 1
make[1]: *** [_module_/home/swaroop/.install_SW/rtl8180-0.21] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.15-25-386'
make: *** [2.6] Error 2

What should I do? 

Regards,

Swaroop Kunduru.

---

### Post by SwaroopKunduru on 2006-06-18
Hi All,


Any one Please help.

Regards,

Swaroop Kunduru.

---

### Post by Lord Illidan on 2006-06-18
Try following instructions here : [https://wiki.ubuntu.com/WifiDocs/Driver/Ndiswrapper?action=show&redirect=SetupNdiswrapperHowto](https://wiki.ubuntu.com/WifiDocs/Driver/Ndiswrapper?action=show&redirect=SetupNdiswrapperHowto)

---

### Post by SwaroopKunduru on 2006-06-18
Lord Illidan,

I went to the site you mentioned and I was on 2nd step 

2.1. With internet access on an Ubuntu computer

If you already have internet access via some other method while logged into Ubuntu, getting

1. Ensure the multiverse and universe repositories are enabled; see AddingRepositoriesHowto

2. Install the ndiswrapper and ndisgtk packages from the Ubuntu repositories. If you don't know how to install applications then you can read [WWW] how to here.


in that 2.1 step when I click the how to I got an error page.

Please help me.

Regards,

Swaroop Kunduru.

---

### Post by Lord Illidan on 2006-06-18
For that 2.1 step, try this link instead : [http://help.ubuntu.com/ubuntu/desktopguide/C/index.html]("http://help.ubuntu.com/ubuntu/desktopguide/C/index.html")

EDIT : I edited the wiki itself, too.

---

### Post by SwaroopKunduru on 2006-06-18
Lord Illidan,

 In step 2.4 substeps 7,8,9 says search for .INF files. I did not find any of them. I have downloaded MA521 NetGear driver zip file specified from "step 2.4/sub step 6".

Please help.

Regards,

Swaroop Kunduru.

---

