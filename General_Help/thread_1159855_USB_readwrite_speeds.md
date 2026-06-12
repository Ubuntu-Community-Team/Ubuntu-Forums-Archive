---
title: "USB read/write speeds"
date: 2009-05-15
forum: General Help
---

### Post by skygazer on 2009-05-15
I am using Hardy 8.04 LTS on my laptop. The read/write speed with a USB pen drive is around 2.5 MBps. When i use the same pen drive on a windows machine, i can copy files much faster (15-17 MBps).  I have calculated average speeds and these are not the  speeds shown by the computer. 

Can anyone help me to increase the read/write speeds?,, what does it depend upon, what are the bottlenecks involved here.. As per the USB 2.0 standards the speeds must be maximum of 60MBps but i am getting only a fraction of that speed.

---

### Post by dcstar on 2009-05-15
> **skygazer said:**
> I am using Hardy 8.04 LTS on my laptop. The read/write speed with a USB pen drive is around 2.5 MBps. When i use the same pen drive on a windows machine, i can copy files much faster (15-17 MBps).  I have calculated average speeds and these are not the  speeds shown by the computer. 

Can anyone help me to increase the read/write speeds?,, what does it depend upon, what are the bottlenecks involved here.. As per the USB 2.0 standards the speeds must be maximum of 60MBps but i am getting only a fraction of that speed.

[LIST=1]
[*]Windows caches write data, so while it can say "completed" a lot of the time it is still actually writing to the device in background (just try removing it after it says it has completed writing a very LARGE file).
[*]The speed of the USB wire connection is irrelevant if the USB device itself can only write at a fraction of it.
[/LIST]

---

### Post by skygazer on 2009-05-15
> **dcstar said:**
> 
[LIST=1]
[*]Windows caches write data, so while it can say "completed" a lot of the time it is still actually writing to the device in background (just try removing it after it says it has completed writing a very LARGE file).
[*]The speed of the USB wire connection is irrelevant if the USB device itself can only write at a fraction of it.
[/LIST]

I have checked it and i remove the disk 5-10 seconds after the file transfer is completed on windows. I dont think the write is still going on in the background when it actually shows as completed. The 700MB file for example took only 40 secs to copy.. So i know my pen drive supports those speeds of 17MBps. The same device slows down with my linux laptop which copied stuff much faster when it used vista.
So there is no problem with my laptop's USB hub and my USB device as well.. Both can support high transfer speeds. Its Ubuntu which makes it slow.

The question is , are there any settings in Jaunty X64 which limit my speed to 2.5MBps.. Please help me figure this out..

---

### Post by skygazer on 2009-05-15
bump****

---

### Post by unclejac on 2009-05-17
I too have this issue, (Painfully slow transfer of data to any kind of USB device) 

I kind of lived with it on 8.10 and now in 9.04 (both 64bit versions) I am determined to solve it.

It's the kind of issue that if you had in windows. You could have solved by installing the drivers for your motherboards chipset etc

However in linux I am unsure where to start, if anyone has any ideas I would be grateful as I am sure also skygazer would be too :D

---

### Post by cyberfin on 2009-08-02
I'm going to bump this one as I too am starting to get annoyed with the USB write speed issue. As other people, I've sat through it in previous versions, telling myself: "Don't worry, they'll fix it for the next one", but just not happening.

Don't get me wrong, I love Ubuntu to bits, but this in particular is getting rather ridiculous.

I mean imagine talking a friend into changing to Ubuntu or giving it a try. A couple of days later he calls you and says: "Hey man, LOVE the OS, I never thought it would be as amazing as it is. One thing though, where can I get the driver for USB 2.0? I have USB 1.1 speeds".

Your answer: "Yeah...about that...". 

(Tilts head down in shame)

---

### Post by upa on 2009-09-11
I can confirm this problem. I am having the same problem in Kubuntu 9.04. Copying about 1GB to a Kingston dt112 takes more than one our (worst, I cancelled it after 45 minutes when it was at 70% more or less, the copy widget said 0B/s of transfer rate. It was stalled!)
It is not a problem of my pendrive because I performed the same copy operation from XP and it took less than 5 minutes.:confused:

I have found that this behavior is specially true with large size files, in my case i was copying the Ubuntu Netbook Remix 9.04 image to a partition in the pendrive 

**Does somebody has heard about to changing some mount options such as sync, -o flush, etc? I have found it but I am not sure if it works.**

Thanks in advance.
Regards,
PS: My hardware is a laptop Dell model 640m, T7200 2GHz, 2GB RAM, 120GB SATA.

---

### Post by P4man on 2009-09-11
Not to dismiss your problems, but just to let you know, i can read/write to my USB stick at ~25Mb/s, which is actually slightly more than its rated speed. That is with jaunty and karmic.

However, I am using Ext3. Perhaps you should rule out an ntfs driver bottleneck by formatting a stick or external drive to ext3 or 4 and see if your transfer rates are still as bad?

---

### Post by zhanglini on 2009-09-11
> **upa said:**
> **Does somebody has heard about to changing some mount options such as sync, -o flush, etc? I have found it but I am not sure if it works.**

[http://ubuntuforums.org/showthread.php?t=432119]("http://ubuntuforums.org/showthread.php?t=432119")

---

### Post by chinmaya_n on 2009-09-11
Yes thats exactly correct what Mr.P4man said!!

You people 've tried to transefer the data to pendrive which is NTFS r FAT formated, just try to format it in ext3 and you can see amazing speeds!!

For ur information i also use pendrives with NTFS b'se many of my frieds are not that addict to Linux as I'm (i too experience the same slower speeds with it) !!

---

### Post by upa on 2009-09-20
Hi again. Sorry for my delay.

This is the entry in /etc/mtab once the usb device is mounted:
**/dev/sdb1 /media/LINUX_USB vfat rw,nosuid,nodev,uhelper=hal,uid=1000,utf8,shortname=mixed,flush 0 0**

There are no entries for this kind of devices in /etc/fstab. Do I have to add one (or many) entries in it? There are no "Properties" menu or submenu in Dolphin for this devices once it is mounted. Neither gparted shows such an option to change or set the asynchronous mode visually. Also, if it works,  I want to mount any usb storage media in the same manner.

Please help with the entry or entries  in /etc/fstab
thanks in advance

---

