---
title: "GRUB loader"
date: 2005-10-24
forum: Desktop Environments
---

### Post by Meksw0ll on 2005-10-24
I installed Ubuntu Hoary Hedge a couple of days ago and whilst it was installing it asked me if I wanted to install GRUB Loader which I know gives you a dual-boot so you can choose whether you wish to boot windows or Ubuntu but for some reason it did not install properly and now I am unable to get back into my windows. I do want to make the complete switch to Linux but I'm having trouble writing the Breezy Badger to CD on Ubuntu here and I'd like to burn it in Windows so I can re-install my Ubuntu frm Hoary Hedgehog to Breezy. 

The problem with burning the CD(I use gnomebaker) is that I downloaded the .iso file frm the Ubuntu site and I open gnomebaker and I select Burn Disc Image and I insert a blank CD but it comes out again. No idea why! But I have other problems why I wish to re-install Ubuntu.

My question now is whether or not it is possible to install the GRUB Loader now, that is, after installing the Ubuntu Hoary Hedgehog?

My other problems are for instance that as of last night whenever I open Firefox and minimize it instead of going to my panel at the bottom it sort of goes to my recycle bin and I can't 're-open' it.


Thanks,
Thomas

---

### Post by heart_reaver on 2005-10-24
Get k3b installed from your synaptics manager 

or go to 

[www.ubuntuguide.org](www.ubuntuguide.org)

there you can find to boot your windows drives, burn iso files by giving command in terminal. 

Also check in Configuration of yours that at what speep it is set. If it set to zero then set as per your cd-r suits to burn the best. Commands can be found on 

[www.ubuntuguide.org](www.ubuntuguide.org)
=======================
For your firefox problem check the spacing lock for minimize window. OR if u can delete that and add new pannel.
==============================

If you want your windows to boot you have to edit grub 's menu.list found in /boot/menu.list

i am posting this not working on ubuntu. so i am not able to paste my grub menu.list file. take cautions in editing file this may lead to grub boot loader to fail to boot your OS

---

