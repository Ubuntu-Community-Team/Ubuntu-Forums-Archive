---
title: "Can't boot to linux after reinstalling vista"
date: 2009-05-22
forum: General Help
---

### Post by uranous on 2009-05-22
Hello,
As on my previous installation of linux (partition with windows) the windows part went very slow, so this time i thought maybe reinstalling vista from the cd would help and so it did. But i cant log in to linux no more, i dont get the option to choose which partition to boot. Im 99% sure that i didnt delete the linux part cause i can see that on "my computer" part of the hard disc is missing (linux partition doesnt show up). Any solutions guys? 
Thnx in advance :)

---

### Post by raymondh on 2009-05-22
Grub may be overwritten by Window's bootloader.  Please see this link

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

Regards

---

### Post by coffeecat on 2009-05-22
A very easy way of reinstalling Grub to the mbr is with [SuperGrubDisk](http://www.supergrubdisk.org). I'm afraid the menus are hardly intuitive, but if you choose the right one, it does rewrite grub stage 1 to the mbr and boot you into your Linux installation. I can't remember which of the several menu choices it is, but the SGD documentation should help.

---

### Post by uranous on 2009-05-25
Thank you both for your help! Super Grub disk didn't work though (or maybe did i something wrong? :P) I booted from the cd, using the option try linux without installing then followed the instructions here: [https://help.ubuntu.com/community/Re...tallingWindows](https://help.ubuntu.com/community/Re...tallingWindows) and voila! :) So, admins this is solved :)

---

