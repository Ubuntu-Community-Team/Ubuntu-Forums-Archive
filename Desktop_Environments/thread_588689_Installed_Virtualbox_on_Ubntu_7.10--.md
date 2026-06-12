---
title: "Installed Virtualbox on Ubntu 7.10--"
date: 2007-10-23
forum: Desktop Environments
---

### Post by masai489 on 2007-10-23
I had been, foolishly, testing out Ubuntu and dual booting to XP for my other apps. But after some digging, I came across virtualbox. I've been unable to find this answer so I'm posing the question. I have Xp on one hard drive and put Ubuntu on another. Is there a way, without reinstalling xp, to get to the xp already installed and setup, using Vbox? If it's already installed there's no image file to get to and that seems to be all that Vbox looks for. I hope I'm being clear in my question. In advance I thank and appreciate you for any help and  guidance anyone can give.:guitar:

---

### Post by masai489 on 2007-10-23
Anyone...? Please? Anyway to make an already installed xp work with vbox?

---

### Post by ubukool on 2007-10-23
Hi,

I used to dual boot Ubuntu and XP on different partitions but then I discovered Virtualbox!  If you want to do this, you have to install XP within Virtualbox so, as far as I know, it won't work across different hard drives.  You can install XP in Virtualbox on your Ubuntu hard drive which will create the imagefile needed for virtualbox to work.

This is a very useful how-to:

[http://www.blog.arun-prabha.com/2007/05/07/installing-virtualbox-and-windows-using-virtualbox-in-ubuntu/](http://www.blog.arun-prabha.com/2007/05/07/installing-virtualbox-and-windows-using-virtualbox-in-ubuntu/)

Good luck!

:cool:

---

### Post by marguz on 2007-10-23
Hello,
You can do what you want in VirtualBox.

In the VirtualBox User Manual go to section 9.9 as it will tell you how to access either the whole hard drive or just a partition of the hard drive.


9.9 Using a raw host hard disk from a guest
Starting with version 1.4, as an alternative to using virtual disk images (as described in
detail in chapter 5, Virtual storage, page 54), VirtualBox can also present either entire
physical hard disks or selected partitions thereof as virtual disks to virtual machines.
  With VirtualBox, this type of access is called “raw hard disk access”; it allows a
guest operating system to access its virtual hard disk much more quickly than with
disk images, since data does not have to pass through two file systems (the one in the
guest and the one on the host).

---

### Post by masai489 on 2007-10-24
> **marguz said:**
> Hello,
You can do what you want in VirtualBox.

In the VirtualBox User Manual go to section 9.9 as it will tell you how to access either the whole hard drive or just a partition of the hard drive.


9.9 Using a raw host hard disk from a guest
Starting with version 1.4, as an alternative to using virtual disk images (as described in
detail in chapter 5, Virtual storage, page 54), VirtualBox can also present either entire
physical hard disks or selected partitions thereof as virtual disks to virtual machines.
  With VirtualBox, this type of access is called “raw hard disk access”; it allows a
guest operating system to access its virtual hard disk much more quickly than with
disk images, since data does not have to pass through two file systems (the one in the
guest and the one on the host).

Thanks you guys for the response. I did read that and keep getting Mandatory parameter -rawdisk missing errors. I'm new to this so forgive me. I can see my windows partition, and I've tried to input what I thought was the path to is and still go the same error. Any ideas?

---

### Post by dilney on 2007-10-24
The rawdisk option is not available in VirtualBox OSE (Open Source Edition).  It is only available in the closed-source edition, which is still free for personal use.

If you want direct access to your hard drive in VirtualBox, you'll have to uninstall VBox OSE and install the other edition from their website.  Then follow the instructions in the manual.

HOWEVER, all the drivers that are configured in your Windows XP may not work in Virtual Box because it virtualizes all the devices.  For instance, your Windows will not see a "nVidia or ATI graphics card", but a "VirtualBox card"...

---

### Post by fdimmling on 2007-10-24
> **marguz said:**
> 
You can do what you want in VirtualBox.


Hi,

I dont believe you can do that. VirtualBox presents the guest system a virtual hardware, e.g. the graphics card, completely different from your actual physical hardware, while your XP on the second harddisk is configured to access the actual physical hardware of your computer. I should say, you can access the harddrive directly but not boot from it as a VirtualBox guest. BTW You would loose all the advantages of a virtual system if you would allow it to directly use the hardware. You would have 2 schedulers running at the same time in parallel, one not knowing of the other.

Friedrich

---

### Post by masai489 on 2007-10-24
Thanks for all of your responses. I tried the PING option instead of having Vbox create the virtual drive. I let that run last night with an option to reboot when done and sure enough it seemed to work. Ubuntu forums are the best out there. Love the knowledge.\

:guitar:

---

### Post by notepad on 2008-02-01
PING option? what do you mean? how did you make it work? i would like to do the same thing as you have if you can explain it.

---

