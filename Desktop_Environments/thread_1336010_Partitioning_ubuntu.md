---
title: "Partitioning ubuntu"
date: 2009-11-24
forum: Desktop Environments
---

### Post by BALJEET OBEROI on 2009-11-24
Hi everybody there 
i am new to ubuntu & have installed ubuntu on my Laptop which was initially having Windows , during partition i partitioned it as 
50 gb for ununtu with mount as  " / "
89 gb for storage of reports with mount as " /home "
30 gb for storage of softwares with mount as " /boot "
howeve after installation i am unable to copy data to mount name " /boot " 
i can only access data from this mount but cannot save or paste data in this mount 
 
can any one help me to store data on my this 30gb partition or can i merge with my home partition for stoage if Yes how ?
 
please help me as i am falling short of storage & i am ubable to use /boot partition
 
thanks in advance

---

### Post by coffeecat on 2009-11-24
First - welcome to the forum, and welcome to the world of Linux/Ubuntu which is utterly, utterly different from Windows. So, to business...

> **BALJEET OBEROI said:**
> 30 gb for storage of softwares with mount as " /boot "

This was a very unwise choice. A separate boot partition is really only needed by experienced Linux users - and most of them don't bother - and is for the kernel and for some of the grub bootloader files **only**. Which means it only needs to be a few tens of megabytes in size. The reason you can't access it is because it is owned by root - as are all system folders. It is easy enough to gain root privileges but let me emphasise one thing:

**Do not store anything in /boot**.

What exactly are the "softwares" that you want to store. If you mean the executables for applications, please do not try to second-guess the package manager. It knows where to put them.

It sounds as though you have brought a number of pre-conceptions from the Windows world with you, and they have misled you. It also looks as though you used the 'Manual' option in the partitioning stage of the installer. That was also an unwise choice for an inexperienced user. As a first-time user you would have been better to have followed one of the guided options.

It is possible to move the contents of the /boot partition to where they should be (in the /boot folder of your root partition), and then to mount that partition somewhere in /media (where it should be) so that you can store stuff in it, but it's not an easy task for a beginner in Linux. I could talk you through it, but I don't think the end result will be optimal for your needs. It's probably better to define exactly what you want in terms of storage, backup your data and reinstall with a more sensible partition layout.

So - before we go any further, what is the nature of the files that you want to store, and how many gigabytes approximately would that be? How big is the Windows C: partition and do you have any other NTFS partitions? Or have you erased Windows from the laptop? It's not quite clear from your post.

---

### Post by BALJEET OBEROI on 2009-11-24
Thanks for your reply 
i would like to know if i want to reinstall ubuntu after backing off the data which partiotn should i use manual or automatic if i want seperate drive for my data

---

### Post by snowpine on 2009-11-24
The minimum number of partitions required for Ubuntu is one: your / (or "root") partition.

Many users choose to create additional partitions (swap, /home, /boot) for specific reasons. If you do not have specific reasons for an unusual partitioning scheme, I suggest letting the Ubuntu installer create the default partitioning scheme automatically.

---

### Post by XubuRoxMySox on 2009-11-24
Hi! Welcome to the wonderful world of Linux!

Most people are well advised to partition as follows:

10-15 gigs for "**/**," 2X your RAM for "**swap**" (I have 512 RAM, my swap is 1 gig), and the rest for "**/home**."

This is especially useful when it's time to upgrade, because you can preserve all your settings and personal files by leaving the "/home" partition unformatted when you re-install or upgrade.

Enjoy!

-Robin

---

### Post by BALJEET OBEROI on 2009-11-24
Thanks for the reply

---

