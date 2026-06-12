---
title: "mount HDD"
date: 2010-12-09
forum: Desktop Environments
---

### Post by Luli on 2010-12-09
HI

l was trying to connect my external HDD and l trying to mount , probably l did it something wrong , now every time when l connect external HDD l see the icon but l can not open 


l need advise please

---

### Post by anglican on 2010-12-09
> **Luli said:**
> HI

l was trying to connect my external HDD and l trying to mount , probably l did it something wrong , now every time when l connect external HDD l see the icon but l can not open 


l need advise pleaseFirst, you need to say exactly what you did to try and mount that HDD, then people might be able to see what you did wrong.

H

---

### Post by karogi on 2010-12-09
read here. i was having same problem.

[http://ubuntuforums.org/showthread.php?t=1612825](http://ubuntuforums.org/showthread.php?t=1612825)

---

### Post by theluli on 2010-12-10
hi

thank but l am not trying to transfer data from external hdd to my desktop l just one have access to external hdd

well l am not sure what l done , thats why l requested a help from this forum

Now when l try to connect ext hdd is showing the icons here but l can not access it ......

---

### Post by Luli on 2010-12-11
This is what l am getting 
HDD is that one that  SPIF301  USB2SATA Bridge because also this name l have at Computer 

lulzim@lulzim-desktop ~ $ sudo tail -s 3 -f /var/log/messages
Dec 11 16:49:00 lulzim-desktop kernel: [  169.787066] sd 4:0:0:0: [sdh] Attached SCSI removable disk
Dec 11 16:50:37 lulzim-desktop sudo: pam_sm_authenticate: Called
Dec 11 16:50:37 lulzim-desktop sudo: pam_sm_authenticate: username = [lulzim]
Dec 11 16:59:07 lulzim-desktop kernel: [  777.250015] usb 1-2: USB disconnect, address 6
Dec 11 16:59:12 lulzim-desktop kernel: [  782.308014] usb 1-2: new high speed USB device using ehci_hcd and address 7
Dec 11 16:59:12 lulzim-desktop kernel: [  782.443191] usb 1-2: configuration #1 chosen from 1 choice
Dec 11 16:59:12 lulzim-desktop kernel: [  782.444911] scsi5 : SCSI emulation for USB Mass Storage devices
Dec 11 16:59:17 lulzim-desktop kernel: [  787.444794] scsi 5:0:0:0: Direct-Access     SPIF301  USB2SATA Bridge  0108 PQ: 0 ANSI: 2
Dec 11 16:59:17 lulzim-desktop kernel: [  787.445325] sd 5:0:0:0: Attached scsi generic sg8 type 0
Dec 11 16:59:17 lulzim-desktop kernel: [  787.450280] sd 5:0:0:0: [sdh] Attached SCSI removable disk

---

### Post by fr3ak.m3 on 2010-12-11
Try parted and see what partitions are there in your harddisk and then use mount command to mount your drives.

---

### Post by Krytarik on 2010-12-11
Try accessing the drive as root: press Alt+F2 and enter "gksudo nautilus".
Very probably that you have to make an entry for the drive/partitions in the file "/etc/fstab". Please post its content and the contents of "/etc/mtab", after you have successfully accessed it with root-rights, which should work.

---

### Post by Luli on 2010-12-14
Hi 

Thanks to all....
But the problem was with physical things , l got nervous and l opened th HDD , and l just connected and start to work 

Thanks

---

