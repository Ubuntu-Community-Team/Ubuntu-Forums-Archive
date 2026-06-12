---
title: "ubuntu 904 dialup"
date: 2009-06-16
forum: General Help
---

### Post by JPman on 2009-06-16
I'll try to make this short.   I've noticed that many flavors of linux no longer come with wvdial via menu for dialup internet access for those of us who have no other option besides $$$satellite$$$.

One of the BAD things about linux are all the variations in package management.   When some standardization is achieved Microsoft will have reason to be worried, not before.  Perhaps one day some kind soul will have "had it up to here" and developed a Universal Package Manager.   Using such a program one can archive favorite apps on a disc at home, just like with M$.

But really all I want now is wvdial in Ubuntu 904.    Why does this have to be so hard for the Ubuntu guys to do for us?    Why do they not see that, by omitting it, a good percentage of Ubuntu users are being "hung out to dry"?

Does anyone know how to help me to get online with 904?

ps   I've tried creating a repository in (904) Synaptic using Ubuntu 804 in the drive.   Didn't work.   Pity.   Sigh!

---

### Post by ad_267 on 2009-06-16
You can get it from [http://packages.ubuntu.com/jaunty/wvdial](http://packages.ubuntu.com/jaunty/wvdial).

Just make sure you have the dependencies listed or install them too.

---

### Post by GeorgeVita on 2009-06-16
Hi **JPman**,

There are 5 .deb packages to install. You could make a zip file with all of them (be sure to check their integrity and **32/64 bit** version).

1. [http://packages.ubuntu.com/jaunty/i386/libxplc0.3.13/download](http://packages.ubuntu.com/jaunty/i386/libxplc0.3.13/download)
2. [http://packages.ubuntu.com/jaunty/i386/libwvstreams4.4-base/download](http://packages.ubuntu.com/jaunty/i386/libwvstreams4.4-base/download)
3. [http://packages.ubuntu.com/jaunty/i386/libwvstreams4.4-extras/download](http://packages.ubuntu.com/jaunty/i386/libwvstreams4.4-extras/download)
4. [http://packages.ubuntu.com/jaunty/i386/libuniconf4.4/download](http://packages.ubuntu.com/jaunty/i386/libuniconf4.4/download)
5. [http://packages.ubuntu.com/jaunty/i386/wvdial/download](http://packages.ubuntu.com/jaunty/i386/wvdial/download)

My .zip file for **i386 32bit** using packages.ubuntu.org (size: 1,04 MB):
[http://acomelectronics.com/GeorgeVita/wvdial_904_i386.zip](http://acomelectronics.com/GeorgeVita/wvdial_904_i386.zip)

Info and checksums included.

Copy and extract .deb files to a USB stick, paste them to the ubuntu 9.04 running pc into **/var/cache/apt/archives/** directory using **sudo nautilus** from terminal.

Double click each .deb icon **in the above order** (1,2,3,4 and finally 5).

If you also need **usbserial** as a driver, read:
[http://ubuntuforums.org/showpost.php?p=7455154&postcount=4](http://ubuntuforums.org/showpost.php?p=7455154&postcount=4)

Regards,
George

EDIT: The "typical" source used (packages.ubuntu.com). I test above and worked with a clean installation (single boot) to HardDisk on my EeePC 1000H. Thanks to **ad_267** for the suggestion! (next post)

---

### Post by ad_267 on 2009-06-16
I would recommend you use the proper Ubuntu packages, not Debian packages. They're not the same thing.

---

