---
title: "Dell Ubuntu Laptop"
date: 2008-08-09
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Kaemon on 2008-08-09
I'm awaiting my shipment of a Dell Laptop with Ubuntu installed on it and I was wondering if it uses the regular Ubuntu repositories to update or does Dell have there own repositories?

I read a while back about dell making there own Ubuntu based OS called Dellbuntu. Has anybody heard any news about that?

---

### Post by xcesarfrancox on 2008-08-09
It does use the official repositories, altought there's a PPA entry for dell's packages

---

### Post by lordhaworth on 2008-08-12
I started using ubuntu through one of those dell pre-installed-ubuntu laptops. One of the first things i did once i started noticing dell influences was install hardy from disk - then you just have good ole ubuntu. 
Its a course of action id probably recommend, and if you want to go back to the dell version you will get a CD with your laptop you can use - you may feel that it defies the point of getting it with ubuntu on in the first place, but your laptop will have been £70 - £100 cheaper and will have never been touched by windows. I cant remember exactly what it was that was annoying me, but I do think i had trouble updating. Hope this helps and good luck with your new laptop and ubuntu

Tom

---

### Post by superm1 on 2008-08-12
> **lordhaworth said:**
> I started using ubuntu through one of those dell pre-installed-ubuntu laptops. One of the first things i did once i started noticing dell influences was install hardy from disk - then you just have good ole ubuntu. 
Its a course of action id probably recommend, and if you want to go back to the dell version you will get a CD with your laptop you can use - you may feel that it defies the point of getting it with ubuntu on in the first place, but your laptop will have been £70 - £100 cheaper and will have never been touched by windows. I cant remember exactly what it was that was annoying me, but I do think i had trouble updating. Hope this helps and good luck with your new laptop and ubuntu

Tom
Please read [http://linux.dell.com/wiki/index.php/Ubuntu_8.04#Dell_OS_Reinstallation_8.04.1_DVD_ISO](http://linux.dell.com/wiki/index.php/Ubuntu_8.04#Dell_OS_Reinstallation_8.04.1_DVD_ISO)
for more information about what is different about Dell's implementation of the Ubuntu install.

In short, you will see a few things added onto it, but nothing significant.

The Dell PPA only contains one package, and it is for when you use an HSF modem.

---

### Post by TimDaniels on 2008-08-13
> **superm1 said:**
> Please read [http://linux.dell.com/wiki/index.php/Ubuntu_8.04#Dell_OS_Reinstallation_8.04.1_DVD_ISO](http://linux.dell.com/wiki/index.php/Ubuntu_8.04#Dell_OS_Reinstallation_8.04.1_DVD_ISO)
for more information about what is different about Dell's implementation of the Ubuntu install.


What's "different" is that it isn't just an install.  It's a return of the **entire disk** to the as-delivered OEM condition, including **erasure** of everything on the disk and a rebuild of the utility and recovery partitions as well as the OS partition.  For Dell's Windows PCs, Dell provides a genuine installation CD/DVD as it would come from Microsoft.  For Dell's Ubuntu machines, you will always get just what you originally got from Dell...  forever.

*TimDaniels*

---

### Post by superm1 on 2008-08-13
> **TimDaniels said:**
> What's "different" is that it isn't just an install.  It's a return of the **entire disk** to the as-delivered OEM condition, including **erasure** of everything on the disk and a rebuild of the utility and recovery partitions as well as the OS partition.  For Dell's Windows PCs, Dell provides a genuine installation CD/DVD as it would come from Microsoft.  For Dell's Ubuntu machines, you will always get just what you originally got from Dell...  forever.

*TimDaniels*
Please keep in mind that the live filesystem included on the Dell recovery ISO is the same live filesystem as the Ubuntu 8.04.1 DVD's.  You can use a normal Ubuntu 8.04.1 CD/DVD instead and get the same resultant system sans the recovery framework.

We *don't* ship dual boot systems, and they are not a "supported" configuration of the recovery framework.  If you want to dual boot, you should just perform a normal non-OEM Ubuntu installation instead.

---

### Post by X40nick on 2008-08-14
I have been thinking about getting one of these, but I need XP alongside Ubuntu. 

Does the Ubuntu CD that comes with the computer have all the drivers there so when I re-install it, with the Dell CD, I get everything working out-of-the-box?

Thank you.

Nick

---

### Post by Kaemon on 2008-08-14
> **X40nick said:**
> I have been thinking about getting one of these, but I need XP alongside Ubuntu. 

Does the Ubuntu CD that comes with the computer have all the drivers there so when I re-install it, with the Dell CD, I get everything working out-of-the-box?

Thank you.

Nick


Theres a program to make your own recovery dvd so that you can reinstall everything. It will also restore the recovery partition. It took over 30 minutes to update but it didn't break anything. When I updated Ubuntu, there were over 950 updates. 

There is also an Ubuntu CD included.

---

### Post by X40nick on 2008-08-15
Thanks, does the CD that comes with it contain all the drivers for, X3100, wireless etc etc etc? 

Thanks,

Nick

---

### Post by superm1 on 2008-08-15
> **X40nick said:**
> Thanks, does the CD that comes with it contain all the drivers for, X3100, wireless etc etc etc? 

Thanks,

Nick
The CD that comes in the box is a standard Ubuntu 8.04 disk and includes everything you need.  You can also use 8.04.1 to avoid the 950 or so extra updates after release.

---

