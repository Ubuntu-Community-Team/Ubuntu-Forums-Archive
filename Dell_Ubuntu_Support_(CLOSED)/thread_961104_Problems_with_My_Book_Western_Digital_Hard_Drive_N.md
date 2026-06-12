---
title: "Problems with My Book Western Digital Hard Drive: Not seen by ubuntu"
date: 2008-10-28
forum: Dell Ubuntu Support (CLOSED)
---

### Post by henrybrad on 2008-10-28
I am running Ubuntu 8.04 LTS on a dell inspiron 1420 and i just got a 1TB back up external hard drive.  The disc is a My Book Western Digital that has an Ethernet port so it can be accessed remotely.  When i plug the disc in via a usb cable, the disc does not mount and it does not show up using "fdisk -l".  Is there any way to mount the disc manually?  

I am planning to clean install on Thursday, with 8.10,  and i want to mirror my disc before that.  Thank you in advance for any help.
-Henry Bradlow

---

### Post by bd_thompson on 2008-10-28
> **henrybrad said:**
> I am running Ubuntu 8.04 LTS on a dell inspiron 1420 and i just got a 1TB back up external hard drive.  The disc is a My Book Western Digital that has an Ethernet port so it can be accessed remotely.  When i plug the disc in via a usb cable, the disc does not mount and it does not show up using "fdisk -l".  Is there any way to mount the disc manually?  

I am planning to clean install on Thursday, with 8.10,  and i want to mirror my disc before that.  Thank you in advance for any help.
-Henry Bradlow

Are you plugging it in directly?  There should be a router between them. Otherwise you need a crossover cable.

---

### Post by henrybrad on 2008-10-28
Thank you for the quick reply.

No i just have a usb cable and i plug the disc directly into my computer's port.  What is a crossover cable?

---

### Post by bd_thompson on 2008-10-28
> **henrybrad said:**
> Thank you for the quick reply.

No i just have a usb cable and i plug the disc directly into my computer's port.  What is a crossover cable?

You mentioned the drive has an Ethernet port.  The World Edition is Ethernet only.  If you have the Home edition, I'm not sure why it is not mounting.  Do you have the Studio edition?  It's formatted for the Mac.  

Please post the exact model you have.

---

### Post by henrybrad on 2008-10-28
Oh, yes i have the world edition.  I thought that it could do both Ethernet and usb but i guess i was wrong.  I will return it and get the other version.  

Thank you very much for your help.

---

### Post by bd_thompson on 2008-10-28
> **henrybrad said:**
> Oh, yes i have the world edition.  I thought that it could do both Ethernet and usb but i guess i was wrong.  I will return it and get the other version.  

Thank you very much for your help.

IMO you should keep it and get a wireless router.  I have two desktops and 4 laptops in the house.  All can access the MyBook simultaneously.

---

### Post by henrybrad on 2008-10-28
Thanks for the advice but i only have one computer so i think ill just go with the usb disk.

---

### Post by lkrubner on 2009-09-11
I just got a Western Digital My Book. I did not realize that these things had problems working with Ubuntu. This one is a half-terabyte. I connect to my machine using the USB cable. It does not automount. 

If I do this:

df -H

It does not appear in the listings. 

When I plug it into my Windows machine, it seems to work fine. 

I thought maybe Western Digital had formatted it funny, so I tried to get the Windows machine to reformat it. It reformatted the whole drive in NFST format. But I still can not get the hard drive to appear when plugged into my Ubuntu machine. Any suggestions?

I should add:

sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80060424192 bytes
255 heads, 63 sectors/track, 9733 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9a3f712c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9356    75152038+  83  Linux
/dev/sda2            9357        9733     3028252+   5  Extended
/dev/sda5            9357        9733     3028221   82  Linux swap / Solaris

Also, when I use gparted, described here:

[http://www.mattcutts.com/blog/format-external-drive-for-linux/](http://www.mattcutts.com/blog/format-external-drive-for-linux/)

It does not recognize the My Book.

The answer given here could be useful to me, if only I could figure out what USB port the My Book was using:

[http://answers.yahoo.com/question/index?qid=20090506223402AAgs5WA](http://answers.yahoo.com/question/index?qid=20090506223402AAgs5WA)

Is there a way I can find out what USB port the hard drive is at?

I suppose this could be the problem:

[http://jguk.org/2009/03/ubuntu-usb-ntfs-filesystem-bugs.html](http://jguk.org/2009/03/ubuntu-usb-ntfs-filesystem-bugs.html)

Although, now I notice that the hard drive will no longer mount on either Ubuntu or Windows. 

How do I get this thing to work?

---

### Post by aridus on 2010-05-05
Dear bd_thompson

'...All can access the MyBook simultaneously.'

Could you please kindly tell me how you have managed this? I have a 1TB MyBook World Edition plugged into our wireless router and want to be able to access it from two Ubuntu pcs. How have you mounted it? I want to be able to backup to it from backintime and use it to share music. 

With grateful thanks

---

### Post by aazan on 2011-01-04
> **henrybrad said:**
> I am running Ubuntu 8.04 LTS on a dell inspiron 1420 and i just got a 1TB back up external hard drive.  The disc is a My Book Western Digital that has an Ethernet port so it can be accessed remotely.  When i plug the disc in via a usb cable, the disc does not mount and it does not show up using "fdisk -l".  Is there any way to mount the disc manually?  

I am planning to clean install on Thursday, with 8.10,  and i want to mirror my disc before that.  Thank you in advance for any help.
-Henry Bradlow

I had the same problem. I proceeded as follows:
Open this drive in Windows OS, run the software that comes with the drive, remove the security. Now it should mount in Linux OS.

---

