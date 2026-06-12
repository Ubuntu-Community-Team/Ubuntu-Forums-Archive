---
title: "Vista to XP and Hardy on Inspiron 1525"
date: 2009-01-03
forum: Dell Ubuntu Support (CLOSED)
---

### Post by pizzipie on 2009-01-03
Hi,

I made a BIG mistake when I bought an Dell Inspiron 1525 for my wife at a "big box store".

It came with Vista, a truly horrible OS. I thought I would be able to install Hardy 8.0.4 on it. HA HA! Next I tried to Re-partition,  format and install XP with the idea of then installing Hardy. No luck it screwed up everything so I couldn't even go back to Vista. I had to call Dell and pay $40 to have them walk me through re-installing Vista. The people at Dell that I talked to won't even discuss Linux!!

So, any idea how I can install XP and Hardy on this machine. 

Thanks in advance, 
Very frusted, RP

---

### Post by ithanium on 2009-01-03
If you are afraid to mess with partitions again you can try installing ubuntu using Wubi, this will install Ubuntu on your PC without the risk of loosing your important data or even damaging some partitions

[http://wubi-installer.org/]("http://wubi-installer.org/")

---

### Post by krnekhelesh on 2009-01-08
> **pizzipie said:**
> Hi,

I made a BIG mistake when I bought an Dell Inspiron 1525 for my wife at a "big box store".

It came with Vista, a truly horrible OS. I thought I would be able to install Hardy 8.0.4 on it. HA HA! Next I tried to Re-partition,  format and install XP with the idea of then installing Hardy. No luck it screwed up everything so I couldn't even go back to Vista. I had to call Dell and pay $40 to have them walk me through re-installing Vista. The people at Dell that I talked to won't even discuss Linux!!

So, any idea how I can install XP and Hardy on this machine. 

Thanks in advance, 
Very frusted, RP

First of all install XP using the Installation CD you may have, using windows XP partition manager create 2 partitions. One partition to keep your windows data and the other for linux.

Then restart your computer with the ubuntu installation CD, install ubuntu on the other partition you created for linux. Thereby you have a system dual booted for both XP and Ubuntu.

I myself use Ubuntu 8.10 on my dell inspiron 1525 and ubuntu detects everything perfectly right from the wireless card to the multimedia keys. If you find that this is too much to do...you can always go for wubi installer which installs ubuntu as a windows program for you to try out.It is simple and clean. Nothing can go wrong with it.

---

### Post by armandh on 2009-01-08
STOP.....

vista has it's own partition editor
it is about the only thing that will change the bullet proof vista partition.

on my wife's compaq v6000 [bottom of the line]

I searched vista and found the partition editor 
I reduced the vista partition leaving the remainder unpartitioned
I installed Ubuntu 8.04 using the "largest unpartition space" guided option.
she now has a dual boot laptop but never uses vista
you may need to hook up wired lan for the updates but with 8.04.1 or 8.10 maybe not.

most computers with pre installed os [even dell with Ubuntu] give one a disk that coppies the OS to the hard drive not an OS instilation disk.

thus without buying or borrowing a real vista instilation disk where fdisk can started [unless the pre installed vista will burn such a utility/boot disk] it is near impossible to wipe vista.

if you do get it wiped install xp first to a partition smaller than the whole. leave the ballance unpartitioned and as before install ubuntu to the unpartitioned space. 

ubuntu will install in an ext3 partition along with a swap partition, both in an extended partition. grub works as expected.

---

### Post by pizzipie on 2009-02-05
When I tried before I used Systemrescuecd with gparted to repartition the hard drive. Seemed to work but xp said it had no hard drive. That is where i tried to go back to vista with real bad luck. I see now that Dell sponsers a web page **([http://www.laptops-drivers.com/dell-laptop/how-to-install-windows-xp-on-dell-inspiron-1525-or-downgrading-vista.html](http://www.laptops-drivers.com/dell-laptop/how-to-install-windows-xp-on-dell-inspiron-1525-or-downgrading-vista.html))**  telling how to "downgrade" from Vista to XP but I don't understand the following: 

Follow this simple Installation  step to downgrade Windows Vista to Windows XP.

a. You have to prepare SATA Driver on your USB Disk. You may get the **Dell Inspiron 1525 SATA ** [HERE]("http://support.dell.com/support/downloads/download.aspx?c=us&l=en&s=gen&releaseid=R166200&SystemID=INS_PNT_PM_1525&servicetag=&os=WLH&osl=en&deviceid=11530&devlib=0&typecnt=0&vercnt=1&catid=-1&impid=-1&formatcnt=1&libid=41&fileid=224400")
b.  You have to prepare** Dell Inspiron 1525 Wireless Card Driver** as well known as [Broadcom BCM 4311]("http://support.us.dell.com/support/downloads/download.aspx?c=us&l=en&s=gen&releaseid=R174291&formatcnt=1&libid=0&fileid=236819").


can you tell me what "prepare SATA Driver on your USB Disk" means? How do you prepare a wireless card driver. I have downloaded all the drivers mentioned in that web site but am stuck as to where/what  to do now.


Again thanks in advance, Rick P.

---

### Post by modena on 2009-02-05
pizzipie,

I don't know the answer to your two questions but:

- XP says it has "no hard drive" because older (maybe all?) XP CDs don't install on SATA drives.
- So get a copy of a free/donation-ware program called nLite and you can easily and quickly make a XP install CD that works with SATA drives.  Search google "nLite XP Sata" and you should find plenty of helpful guides.
- Like you, I also used GParted to get rid of all the Dell partitions on my 1525, and that worked fine.  So if re-installing Vista changed the partitions back to having the dell partitions, you can just get rid of them again before installing XP.
- You should be able to install XP without any problems using the *nLite* XP CD.
- After that you should also be able to install ubuntu for the dual boot without any problems (depending on which wireless card you have).

Hope that helps.

---

### Post by pizzipie on 2009-02-08
Thanks Modena,

I'm still trying to get up the nerve to get into this all again. Will let you know what happens.

R.

---

### Post by carusoswi on 2009-02-08
> **pizzipie said:**
> Thanks Modena,

I'm still trying to get up the nerve to get into this all again. Will let you know what happens.

R.

I was just initiated to the Vista nightmare this afternoon.  My son's Gateway laptop, about 14 months old, suffered a sudden HD crash.  We purchased another and installed it.  He installed Vista from his OEM disk.  Almost immediately, the new installation started to act up.  I offered to set him up with a dual boot XP/Ubuntu installation.  To my surprise, nothing I did would allow the XP install disc to detect his new drive.  We were running out of time, so I set him up with his original Vista and a dual boot to Ubuntu.

I will mark this thread and we will give it another go on another day.

Typical of the Windows side of things to fix it so that you aren't free to do what you wish, even when it is all legal (I own an extra copy of XP Pro that has never been installed).

I will never own a machine that has Vista installed.

Caruso

---

### Post by armandh on 2009-02-09
it is going to get worse as ever newer hardware needed for the setup; SATA, video, wireless, etc has no driver available for [the nolonger supported] XP.

---

