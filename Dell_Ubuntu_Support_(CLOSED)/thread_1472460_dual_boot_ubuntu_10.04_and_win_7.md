---
title: "dual boot ubuntu 10.04 and win 7"
date: 2010-05-04
forum: Dell Ubuntu Support (CLOSED)
---

### Post by me2030581 on 2010-05-04
hi

i tried to install ubuntu 10.04 on my dell studio 15 by usb flash drive

every thing go fine 

grub boot loader install in my single hard drive's MBR

when i reboot it show grub and i can boot ubuntu or win 7

when boot ubuntu its fine no problem but when i boot win7 first it will boot fine but when restart it grub will not show 

error show "no moudle name found"

i tried install grub again but same thing happens 

i think win7 remove grub when it reboot

my partition are

1 sda1 Dell Utility fat16
2 sda2 recovery ntfs boot flage
3 sda3 Os
4 sda4 extended
5 sda5 / ext4
6 sda6 swap

i resize partition in win 7 to install ubuntu

anyone have any idea

thanks

---

### Post by reiki on 2010-05-04
In Windows 7, I had to remove Windows 7 DataSafe. (Add/Remove Programs)

It overwrites a part of Grub. After I removed that one program, no more problems.

BEFORE I removed that program, every time I booted windows and then tried to restart, I had a messed up Grub and had to reinstall Grub.

---

### Post by me2030581 on 2010-05-04
thanks thats work

---

### Post by mrsato on 2010-05-07
What is DataSafe, and how do I uninstall it?

---

### Post by garvinrick4 on 2010-05-07
Dell and screwing with Microsofts software and putting its own utility in sda1 makes a mess of everything that is where the partition for mbr should be. sda2 Win OS maybe 3 the extended and sda4 recovery partition. There is your 4 Primarys and all the Linux you need inside the extended. What good is the sda1 of Dell when you already have a recovery in 7 if needed. Put your grub in sda and make a nice mbr in sda1. DELL makes it so difficult. Are they still giving you a extra disk for drivers instead of on the install disks? And is sda1 in DELL still a hidden partition in there version of Windows? Pain in the rear as I see it.
Dell should just make your machine give you your disks and be done with it.

---

### Post by isale8888 on 2010-09-18
[reiki]("http://ubuntuforums.org/member.php?u=35792")

thank you so much, I have to use more often a linux OS so I chose ubuntu and wanted to do dual booting alongside windows 7 (dell inspiron 1440) and I was having the same problem as [me2030581]("http://ubuntuforums.org/member.php?u=237000")

thanks a lot again, and hoping to be useful in a short term for the rest of the forum!!!

---

