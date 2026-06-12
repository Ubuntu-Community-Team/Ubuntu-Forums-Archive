---
title: "ATI non open source driver"
date: 2006-05-22
forum: Desktop Environments
---

### Post by youthforlinux on 2006-05-22
hi im a newbie to ubuntu and linux and i was wondering how to install the proprietary drivers for my ATI, its either a 9200 or 9500.  or is there another way to get 3d acceleration

---

### Post by tigrux on 2006-05-22
The kernel module is in linux-restricted-modules.

The xorg support is un xserver-xorg-driver-fglrx

---

### Post by youthforlinux on 2006-05-22
Ok I installed it and i was wondering if there waz any configuration that needs to be done after that?

---

### Post by halfvolle melk on 2006-05-22
Method 2 of the below link worked wonders for me (breezy):
[http://wiki.cchtml.com/index.php/Ubuntu_Breezy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Breezy_Installation_Guide)
If you use Dapper, this might work equally nice:
[http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide)

---

### Post by youthforlinux on 2006-05-23
Thanks it worked great

---

### Post by rottym on 2006-05-23
I have a ATI Radeon Mobility 9200 (Compaq X1000) and I tried both methods listed above; on the first method the resolution is stuck at 1280x768 ... at the second when I reboot the screen is all messed up with horizontal lines :(  All the resolution settings from xorg.conf remained the same as in method 1 ... Can anyone encountered a similar problem??

Thanks a lot !

---

### Post by halfvolle melk on 2006-05-23
I would suggest you stick to the first method, see if you can get that working again, and then post your xorg.conf. From my ultra limited experience in mucking about with xorg.conf + low resolution I would guess that the horizontal and vertical refresh rates are not set properly.

---

