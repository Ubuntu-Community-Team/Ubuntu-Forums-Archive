---
title: "Partitioning"
date: 2009-05-21
forum: General Help
---

### Post by DarthCookie on 2009-05-21
Hello my fellow Linux users! This is my first post in this forum.

I just recently bought Asus Eee 1000H with windows XP. After a few days of experiment I have a great opinion and I think I made an decent buy. 

I also installed Ubuntu 9.04 UNR which I think is really nice too. It tooks me some time to get used to the different enviroment from the desktop Ubuntu but I think Canonical did a great job bringing on this netbook enviroment.

So here goes the problem:
I want to format the hard drive, partition it in 3 parts. 
C so I can have Ubuntu UNR, approximately 60GB.
D so I can have Windows XP, approximately 60GB and
E which covers the rest of hard drive so I can use it for data.

So which path should I choose to do that? Have Ubuntu installed first or XP? Does it makes any differnce? And is it possible to do it cause I read in some posts that for installing XP all over on Eee I have to use the excact same partitioning that it had by factory default. Here's a link saying just that:
[http://myeeeguides.wordpress.com/2008/10/15/eee-pc-1000h-recovery-from-usb-flash-drive/](http://myeeeguides.wordpress.com/2008/10/15/eee-pc-1000h-recovery-from-usb-flash-drive/)

Thank you!

p.s.1 I don't want to use Wubi.
p.s.2 I have posted a relative thread in Asus Forums. Here's the link:
[http://vip.asus.com/forum/view.aspx?id=20090521123349424&board_id=20&model=Eee%20PC%201000H/XP&SLanguage=en-us](http://vip.asus.com/forum/view.aspx?id=20090521123349424&board_id=20&model=Eee%20PC%201000H/XP&SLanguage=en-us)

---

### Post by madmaxou on 2009-05-22
I'd first install windows because the ubuntu partioning programm is more intelligent. While installing ubuntu you're able to make your partitions.

---

### Post by dandnsmith on 2009-05-22
> **DarthCookie said:**
> I just recently bought Asus Eee 1000H with windows XP.

I also installed Ubuntu 9.04 UNR .

So here goes the problem:
I want to format the hard drive, partition it in 3 parts. 
C so I can have Ubuntu UNR, approximately 60GB.
D so I can have Windows XP, approximately 60GB and
E which covers the rest of hard drive so I can use it for data.

So which path should I choose to do that? Have Ubuntu installed first or XP? Does it makes any differnce? And is it possible to do it cause I read in some posts that for installing XP all over on Eee I have to use the excact same partitioning that it had by factory default. Here's a link saying just that:
[http://myeeeguides.wordpress.com/2008/10/15/eee-pc-1000h-recovery-from-usb-flash-drive/](http://myeeeguides.wordpress.com/2008/10/15/eee-pc-1000h-recovery-from-usb-flash-drive/)

I'd query the 'need to format the HDD' - if you've both XP and UNR installed, you could remove UNR, use gparted to modify the partition setup, and format any newly created partitions, and then install UNR again.

Biggest drawback (but not nearly as great as reinstalling XP) is the need to create a bootable USB stick with gparted.

---

### Post by DarthCookie on 2009-05-22
Well dandnsmith,

You see, that's a very good idea EXPECT I already did a very stupid thing. I tried to partition the HDD with the Ubuntu UNR boot USB and as a result of an amatuer I deleted important files (I guess..) and now Eee can't even boot! When I turn it on I get the following message:

"GRUB Loading stage1.5.

GRUB loading, please wait...
Error 15"

I kinda paniced at first but then I decided to do the following steps:

1)Make a bootable Windows XP USB Flash Disk
2)Install XP
3)Partition the HDD via Windows the way I wanted from the biggening 
4)Install Ubuntu UNR
5)Celebrate!

Which is the simpler way of doing things and I guess I'm really stupid not doing that. #-o

And again another problem appears right on step 1!! 

All blogs/sites recomend using peToUSB to make a USB bootable for XP. But peToUSB not only does NOT recognise my *Patriot Xporter 8GB* USB but also does NOT recognise another 3 USBs I borrowed from by friends. A *SanDisk Cruzer* 2GB, a *Kingston DataTraveler* 4GB and a Kingston DataTraveler 8GB. 

I tried formating the USBs from FAT32 to NTFS via the default program Windows Vista has but nothing changed. 

So here I am, stuck on step 1, with my brand new Eee 1000H turned off and desperate for help... :lolflag:

---

### Post by DarthCookie on 2009-05-23
Guys problem solved!

I followed the instructions of the member *eperamak in eeeuser.forum.com *and everything is fine.

For those having the same problem check the following link to see what's up. 

[http://forum.eeeuser.com/viewtopic.php?pid=581345#p581345](http://forum.eeeuser.com/viewtopic.php?pid=581345#p581345)

---

### Post by dandnsmith on 2009-05-23
Glad to hear it's solved.

Interested to hear about the problems making the USB sticks bootable - I've only really tried using syslinux, so don't know if I'd have the same problem (those types are really common!)

---

### Post by siriusb_hun on 2009-05-23
With [unetbootin]("http://unetbootin.sourceforge.net/") I haven't experienced any problems. You may want to have a look at it.

---

### Post by dandnsmith on 2009-05-25
Thanks for that - I've used unetbootin a few times, and it uses syslinux to install the boot stuff (look at it's scripts)

---

