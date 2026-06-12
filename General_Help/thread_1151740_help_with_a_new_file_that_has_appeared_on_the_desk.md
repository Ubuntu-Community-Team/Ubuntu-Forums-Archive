---
title: "help with a new file that has appeared on the desktop"
date: 2009-05-07
forum: General Help
---

### Post by viaciofano on 2009-05-07
hi, i am learning all the time and new to linux. i also bought a android phone also. following the instructions to upgrade eclipse i started to download the zip files and upgrade packages.
using package manager
now i have a file appear on my desktop with the letters OS
properties show a folder with 428 items totaling 1.9gb
msdos

if i click the file browser i see
casper
debs
dists
docs
grub
isolinux
misc
pool
preseed
scripts
md5sum.txt
ubuntu


what have i done? how do i go back??
thanks

---

### Post by salvachn on 2009-05-07
Have you installed Ubuntu inside Windows? The contents seem like those of an Ubuntu ISO!

---

### Post by salvachn on 2009-05-07
It is possible that it could be a shortcut or a link to a CD. You may have mounted a CD or an ISO.

---

### Post by viaciofano on 2009-05-07
how do i remove the file? safely? i am not sure how i find out what the file is?

---

### Post by salvachn on 2009-05-07
If it shows as a CD icon, then right click and unmount it. Yes, you can try deleting with normal privileges. If you cannot, then see if you've connected any other device.

---

### Post by salvachn on 2009-05-07
Do a ls -l in /home/user/Desktop and paste it here.

---

### Post by viaciofano on 2009-05-07
thanks for your help
i dont think the file is visible as i have downloaded other files for my android app

total 252736
-rw-r--r-- 1 viaciofano viaciofano 162938845 2009-05-07 10:28 android-sdk-linux_x86-1.5_r1.zip
-rw------- 1 viaciofano viaciofano   1539375 2009-04-25 12:39 Marlon_ST_Guide_1.pdf
-rw-r--r-- 1 viaciofano viaciofano   9181622 2009-05-04 12:51 ota-radio-2_22_19_26I.zip
-rw-r--r-- 1 viaciofano viaciofano  37983095 2009-05-04 12:53 signed-dream_devphone-img-147201.zip
-rw-r--r-- 1 viaciofano viaciofano  46867722 2009-05-04 12:58 signed-dream_devphone-ota-147201.zip
viaciofano@dell-desktopi530:~$

---

