---
title: "todays kernel update .26 killed my ATI display driver"
date: 2006-09-14
forum: Desktop Environments
---

### Post by stefan1975 on 2006-09-14
i have the same problem mentioned in another thread about Nvidia with my ATI card. 

the kernel update broke my system! I have an ATI mobility with the fglrx drivers installed. After the .26 k7 kernel update the drivers aren't running anymore so no more compiz for me. I tried the 386 drivers instead but same problem.

and yes i have uninstalled the old fglrx drivers and after the kernel update installed the latest .26 fglrx drivers through synaptic AND rebooted the system (again).

any help would be really appreciated, i just love my Compiz and want it back.

stefan

---

### Post by Ramses de Norre on 2006-09-14
Same thing here.. No fglrx and no direct rendering since the kernel upgrade..
Anyone who knows a solution?

---

### Post by jdong on 2006-09-14
New restricted modules are being uploaded and will land on mirrors soon.

---

### Post by whiterussian on 2006-09-14
Depending on how you installed your ati drivers, repositories with mesa or the proper ATI drivers, you may have to rebuild them for your new kernel. If you build them from ATI's proprietary ones on their site, I have had to rebuild them for nearly every kernel version, well, until I got NVidia.

Can be found here:

[http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide#Method_2:_Generating.2FInstalling_Ubuntu_packages_for_the_8.28.8_drivers_in_Ubuntu_Dapper_Manually](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide#Method_2:_Generating.2FInstalling_Ubuntu_packages_for_the_8.28.8_drivers_in_Ubuntu_Dapper_Manually)

Hope its of some use.

---

### Post by tophfisher on 2006-09-14
This bit me too... MAN THIS SUCKS.. This is my work system... DANG IT.

Its an easy fix to go change the driver from nvidia to nv and fix the issue, but the Windows people in the office laugh at me when they see what looks like a "Linux Crash".

Bummer.. ](*,) ](*,) =D> ](*,) ](*,) 
-Chris

---

### Post by whiterussian on 2006-09-14
Well, at least we get error messages, and know why it crashed. :) 

If the new fglrx drivers are in the repository, go get em'. But again, recompiling the ATI proprietary ones takes a good 5 minutes, and then you have proper 3d acceleration.

---

### Post by Ramses de Norre on 2006-09-14
Restricted modules are updated;) I've got everything working here.

---

### Post by Revolution on 2006-09-14
Can I offer some wisdom?

Dont blindly update.
I always wait a few days and check here often for reports from others that have already updated.

So far I've avoided any 'accidents'.
As my Ubuntu machine is my 'work' machine I take great care with any updates.

---

### Post by mdz on 2006-09-14
This is the same issue as described in [http://launchpad.net/bugs/60433](http://launchpad.net/bugs/60433) and [http://www.ubuntuforums.org/showthread.php?p=1500193](http://www.ubuntuforums.org/showthread.php?p=1500193) and has been addressed in the latest updates.

We apologize for the problems which have been experienced as a result of this error.

---

