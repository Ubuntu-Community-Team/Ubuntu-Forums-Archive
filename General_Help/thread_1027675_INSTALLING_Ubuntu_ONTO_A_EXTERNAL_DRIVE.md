---
title: "INSTALLING Ubuntu ONTO A EXTERNAL DRIVE"
date: 2009-01-01
forum: General Help
---

### Post by hatewindows on 2009-01-01
Hello and happy NEWYEAR--I just wanted to know if i can install ubuntu 8.10 onto an external USB hd and if so what is the easy way it can be done..

I would also like to know--If i do install onto a USB Hard drive--can i plug the drive into any PC or does ubuntu  only work with the hardware from the computer that installed to the external drive? Thanks and happy new year to all.. MARK

---

### Post by logos34 on 2009-01-01
Here, try this (works for usb flash as well as usb hdd)

[http://www.pendrivelinux.com/2008/04/14/ubuntu-804-usb-hard-drive-install/](http://www.pendrivelinux.com/2008/04/14/ubuntu-804-usb-hard-drive-install/)

most of the time it works on other machines (video might need some config though)

---

### Post by adog317 on 2009-01-01
you should be able to install intrepid (or any other distro) to an external hd by using [UNetbootin]("http://www.google.com/url?sa=t&source=web&ct=res&cd=5&url=http%3A%2F%2Fsourceforge.net%2Fprojects%2Funetbootin%2F&ei=RVtdSY_KPJGYsAOag6icDQ&usg=AFQjCNHLAap-hdy9tb14e6oIEKyaaLu4wA&sig2=NIvmsnrNyRMQAZ4Xg_hEvQ") and specifying it to install onto your external hd. when you are powering on your comp, hit the key that lets you select your boot media (on my comp its F12) and select "USB Disk" or something like that.

---

### Post by louieb on 2009-01-01
By default the installer will put the GRUB stage1 program in the MBR of the 1st drive in the boot order. ( Probably your internal drive) The pendrive tutorial prevents this by have you unplug all your internal drives.  

That is the sure way to put the GRUB stage1 program on the MBR of your external drive.  If you feel like you know what your doing then on the summary page you can select the external drives MBR  by pressing the advanced button. Then pick it from the drop down list.       

Ubuntu should boot then from any computer you have the external drive plugged into but there is no guarantee that things like screen resolution would be what you want or wireless internet access would work right out of the box. 

Happy New Year to you too. and Good Luck.

---

### Post by hatewindows on 2009-01-01
Thanks for all the info... Mark

---

