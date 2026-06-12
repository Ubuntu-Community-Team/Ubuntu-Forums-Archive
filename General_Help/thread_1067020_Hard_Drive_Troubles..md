---
title: "Hard Drive Troubles."
date: 2009-02-11
forum: General Help
---

### Post by ZettaGeek on 2009-02-11
Hello Linux Community!

I recently switched from a 30GB hard drive, to a 60 GB hard drive. Before on my 30GB, I had it partitioned so I could duel boot Windows 2000 and Mandriva Linux. 

Later, I switched out the 30GB for 60GB so I could have more room for storage. But, the 60GB is a used hard drive from a Windows XP computer and it has a "bad sector".

This is how I have *tried* to set up my computer, I first installed Windows 2000, letting it use the full 60GB for a NTFS partition that I would later resize using the Mandriva installer. I installed Windows, then rebooted the computer with the Mandriva Live CD. Needless to say, when I try to install Mandriva on the hard drive, it tells me I have a bad sector and need to run "ntfsclone".:confused:

After getting tired of trying to figure out how to do this, I inserted an Ubuntu live cd to try and install it, it won't even boot as a live cd and is still displaying a whole bunch of I/O and SQUASHFS errors.

Any help on getting either of these distros of Linux installed would be fantastic.

~Josh

---

### Post by cariboo on 2009-02-11
Go to the hard drives manufacturers web site and download their diagnostic software, it will do a drive fitness test and repair or lock out any bad sectors.

Jim

---

### Post by Dr Small on 2009-02-11
It seems strange that the LiveCD wouldn't load. You can try what cariboo907 suggested. What is the brand of the hard drive (if it has one)?

Dr Small

---

### Post by ZettaGeek on 2009-02-11
> **cariboo907 said:**
> Go to the hard drives manufacturers web site and download their diagnostic software, it will do a drive fitness test and repair or lock out any bad sectors.

Jim

Hey Jim,

This is an IBM Deskstar Model IC35L060AVVA07-0 7200 RPM, I will begin searching for a sectors utility for it.

Levi,

I can get the Mandriva live CD to boot, it just won't let me partition or install.

~Josh

---

### Post by Peter09 on 2009-02-11
There is most probably a scratch or write error on the Ubuntu CD which is why it will not boot.

---

### Post by ZettaGeek on 2009-02-11
> **Peter09 said:**
> There is most probably a scratch or write error on the Ubuntu CD which is why it will not boot.

I would think that except that my brother just installed Ubuntu on his computer using this CD and it works on his machine with no problems.

I have also tested this CD on the computer I'm on right now and it works here as well.

---

### Post by ZettaGeek on 2009-02-12
Problem Solved! 

I downloaded the Drive Fitness Test cd image and burned it to a disc. With that, I was able to erase my MBR and fix the bad sectors on my hard drive. :-)

Since then I tested the Ubuntu Live CD and it works great, and I was able to re-install Mandriva Linux.

Thanks for your help,
Josh

BTW, I don't recommend ever buying anything made by IBM since there tech support is terrible. I could not even find documentation on my drive at there website.. :lolflag:

---

### Post by Dr Small on 2009-02-12
> **ZettaGeek said:**
> Problem Solved! 

I downloaded the Drive Fitness Test cd image and burned it to a disc. With that, I was able to erase my MBR and fix the bad sectors on my hard drive. :-)

Since then I tested the Ubuntu Live CD and it works great, and I was able to re-install Mandriva Linux.

Thanks for your help,
Josh

BTW, I don't recommend ever buying anything made by IBM since there tech support is terrible. I could not even find documentation on my drive at there website.. :lolflag:
Great! Glad you got your problem fixed :D

---

