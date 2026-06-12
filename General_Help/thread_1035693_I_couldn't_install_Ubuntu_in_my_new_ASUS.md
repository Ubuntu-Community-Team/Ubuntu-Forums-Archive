---
title: "I couldn't install Ubuntu in my new ASUS"
date: 2009-01-10
forum: General Help
---

### Post by MIH1406 on 2009-01-10
Hi,

I have bought a new laptop ASUS F8VR $960 with Windows Vista Premium but I want to install Ubuntu instead. The problem that I cannont install Ubuntu?? The CD runs OK and I followed the instructions and complete the installation wizard when I click Install it started to install but after a while I found a black screen with repeated message!!

Thanks,

---

### Post by sp0nge on 2009-01-10
What is the repeated message?

---

### Post by Lod on 2009-01-10
I had a similar problem with my Asus M50Vn laptop. In my case it had probably something to do with the recovery partition Asus had made on it. It was the first partition on my hard drive and had the Hidden Fat32 partition type. I believe that during the install Grub is installed to the first partition, maybe it can't handle this kind of partition type?

Anyway, I made a backup of the recovery partition and afterward removed all partitions with fdisk, did a new install and now Ubuntu's working fine. (Un)fortunately I'm not able to install Windows Vista at all anymore.:cool:

---

### Post by MIH1406 on 2009-01-11
I cannot give you the repeated message, I have to retrieng installing ubuntu to get to that message.

Some of my friend told me about something called SATA and its drivers to allow another OS to run on that thing (SATA). Bcause SATA just accept Vista.

Is there a SATA driver for AUSU to install Ubuntu???

Thanks,

---

### Post by Lod on 2009-01-11
Maybe your friend meant Vista just accepts SATA instead of SATA just accepts Vista. Linux should not have any problems with sata drives at all.

---

### Post by MIH1406 on 2009-01-11
In another word,
He tries to install XP on his new laptop but he couldn't until he found in the internet something called unlock sata protection to install XP instead of "recovering your Vista which ships with the laptop's CDs".

Thanks,

---

### Post by MIH1406 on 2009-01-11
Here is the repeated message:
[  818.021242] VFS: busy inodes on changed media
[  946.020415]
the number changes every second, I left this black screen with messages more that 5 hours and nothing changed??

I followed the same steps in my old laptop and Ubuntu installed correctly!

I am waiting a solution

---

### Post by MIH1406 on 2009-01-11
another messages!!
[#]SQUASHFS error: sb_bread failed reading block [#]
[#]SQUASHFS error: unable to read fragment cache block [#]
[#]SQUASHFS error: unable to read page, block [#]
then repeating the first one!!

---

### Post by MIH1406 on 2009-01-11
Finally:

I changed in the BIOS:
'SATA Operation Mode' from 'Enhanced' to 'Compatible'

and this solved the problem, but is there any disadvantages of this option!

Thank you everyone tries to help me

---

