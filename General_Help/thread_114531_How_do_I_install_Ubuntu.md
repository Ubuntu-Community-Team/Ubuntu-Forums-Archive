---
title: "How do I install Ubuntu ?"
date: 2006-01-08
forum: General Help
---

### Post by motorsep on 2006-01-08
I am gonna receive hardware upgrade next week, which includes new 80Gb HDD.
I would like to have WinXP and (K)Ubuntu installed. I use NTFS for XP.

1. How do I do that? 
2. What do I install first?
3. Do I have to create separate partitions for XP and Linux?

---

### Post by o_fortuna on 2006-01-08
[QUOTE=motorsep]I am gonna receive hardware upgrade next week, which includes new 80Gb HDD.
I would like to have WinXP and (K)Ubuntu installed. I use NTFS for XP.

1. How do I do that? 
2. What do I install first?
3. Do I have to create separate partitions for XP and Linux?[/QUOTE]
The Ubuntu installer can do everything you need to install. You should install Windows first, because it's wierd that way :) . It has something to do with the boot manager (letting you boot multiple OSes), which Windows messes up when you install it after Ubuntu (or something like that). After XP is intstalled, just stick in the (K)Ubuntu install CD and you're ready to go.

And yes, you must create separate partitions for XP and Linux. The Ubuntu installer will do this really easily though, and will help you resize the NTFS partition that the Windows installer created for XP.

---

### Post by ptmurphy on 2006-01-08
[QUOTE=motorsep]I am gonna receive hardware upgrade next week, which includes new 80Gb HDD.
I would like to have WinXP and (K)Ubuntu installed. I use NTFS for XP.

1. How do I do that? 
2. What do I install first?
3. Do I have to create separate partitions for XP and Linux?[/QUOTE]


You will need to install XP first.  It will overwirte you master boot record (MBR) on the hard drive and that would mess up your dual boot that ubuntu set up with Grub.

I would recommend partitioning you hard drive with the windows disk and setup a partition to whatever size you want XP to use.  Leave the rest unpartitioned.  Let XP install into the partition it created.

Then run the ubuntu install disk and it will automatically install itself (by default anyway) into the unpartitioned space.

---

### Post by Sef on 2006-01-08
I wrote up this on setting up  XP and Linux as a dual boot:


> 1) Install Windows first

2) When it gets to partitioning, use 'manually partition' (similar words-it's the bottom option.) Below is from a previous post of mine:


Quote:
Re: Partitioning Problems - 5 Days Ago 
I) If there is no free space on the disk, do this:

A) Highlight the partition you want to shrink. 

B) Highlight the disk size. 

C) Erase the numbers on the screen and write in the new size of the partition - XX.X GB . 

- Don't forget to put GB

4) Click on the button. (I think it says 'OK'.)

5) Then click on 'Done Partitioning This Disk' (or something similiar, it's the top option.)

II) Two Partitions Now

A) One which says NTFS and one that says Free Space.

1) NTFS is the XP partition
2) Free Space can used to set up Ubuntu Linux.

-) It's a good idea to maually partition, and set up a /home directory, so when you upgrade Ubuntu, your files and settings won't be overwritten. 	

3) Read this first before installing. It explains with pictures how to install a dual boot. [http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)


---

### Post by aysiu on 2006-01-08
[QUOTE=motorsep]I am gonna receive hardware upgrade next week, which includes new 80Gb HDD.
I would like to have WinXP and (K)Ubuntu installed. I use NTFS for XP.

1. How do I do that? 
2. What do I install first?
3. Do I have to create separate partitions for XP and Linux?[/QUOTE] See the fifth link of my sig.

---

### Post by motorsep on 2006-01-09
Thaks guys!
Does (K)Ubuntu see NTFS partition after installation?

---

### Post by Thirsteh on 2006-01-09
I cannot believe that people inhere don't tell users who want to dualboot that they have to defrag...

motorsep, yes, you will be able to view your windows partition in Ubuntu, but before you install Ubuntu you need to do something extremely important, defragment your drive in windows. If you don't do this and install Linux on the same drive you will not be able to boot Windows after the Linux installation. And nah it's not Ubuntu's fault :)

---

### Post by motorsep on 2006-01-09
Hmm.. Thanks for advice. Will it be better if I create two partitions, one for WinXP and one for (K)Ubuntu?

---

### Post by frodon on 2006-01-09
Yes, here is a a step by step guide, which may help you : [http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

---

### Post by ptmurphy on 2006-01-09
[QUOTE=Thirsteh]I cannot believe that people inhere don't tell users who want to dualboot that they have to defrag...[/QUOTE]

If you setup an XP partition and leave part of your disk unpartitioned to later install Ubuntu to, why would you need to defrag your XP partition before installing Ubuntu into a partition that has never known anything about XP?

---

### Post by Azriphale on 2006-01-09
As ptmurphy says, if you create a windows partition that does not take up your whole drive, Ubuntu will not touch it and there will be no problem. My various computers setups (multiple reinstalls of Windows and various Linux distros through the years) is proof of this. You just need to set upi the windows partition in the very beginning, and everything will be fine. Just make sure you leave enough unpartitioned space on the drive for Ubuntu.

---

### Post by motorsep on 2006-01-09
How much is enough for (K)Ubuntu? Is 20Gb enough to install it and have various programs like GIMP, OpenOffice, Blender3D, etc. and have space left for projecs' files?

---

### Post by Azriphale on 2006-01-09
20GB is enough, I'm sure. I used to have only 10GB for Linux until I decided to migrate almost completely. But 20GB will give you a little more flexibility, allow you to play with more software if you want to.

---

### Post by motorsep on 2006-01-09
Thank you.

---

### Post by Azriphale on 2006-01-10
Sure. Enjoy :)

---

