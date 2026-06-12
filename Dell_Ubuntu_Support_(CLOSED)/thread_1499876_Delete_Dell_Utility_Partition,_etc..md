---
title: "Delete Dell Utility Partition, etc."
date: 2010-06-02
forum: Dell Ubuntu Support (CLOSED)
---

### Post by tanha on 2010-06-02
If I delete the Dell Utility partition, and the other dell partition with the system restore, install ubuntu, let grub be the bootloader, will I have any problem booting into windows? That is, is windows dependent on either of these two partitions for booting?

---

### Post by atomizer on 2010-06-02
Your Windows will work as usual. But you won't be able to recover Windows when something goes wrong (or you will need an windows install cd or the recoverycd (that you made when you powered on the laptop for the first time))

---

### Post by Citadel1980 on 2010-06-02
As long as the Windows MBR (master boot record) is on the C:\ hard drive (sda1 or hda1) then you should be fine. 

I would recommend though that you use a backup tool like Acronis or Macrium Reflect Free to make copies of all your partitions including the MBR.

I had a Dell Mini 10 with Win XP on it and faced the same issues. I wanted to install Ubuntu 9.04 and wanted to make sure I could restore the netbook to factory condition - out of the box. I used Macrium Reflect Free to Backup the Dell Utility partition, the Dell Restore partition amd the Windows XP partitions. Then I used Gparted to reconfigure (resize/move) my Windows XP C:\ drive - sda1 and made a / or boot partition, home and a swap partition for Linux.

Everything worked fine. When I sold the Dell Mini 10 I wiped the hard drive of all partitions with Gparted and used Macrium Reflect Free to reinstall the Dell Utility partition, the Dell Restore partition and the Windows XP partition.

Gparted can be downloaded as an ISO file and burned to CD. Macrium Reflect Free is a Windows program but it uses Linux on a CD to help you restore your partitions.

If you use this method, make sure you write down the exact sizes of all your partitions. Most ghost imaging software only allows you to restore partitions to a SAME SIZE or LARGER partition not to a SMALLER partition.

I hope this helps.

---

### Post by tanha on 2010-06-02
Thanks for the reply guys. I will use clonezilla to clone the hdd. Then, I'll dual boot ubuntu. I have no need for the recovery partition or diagnostic utils. thanks!

---

