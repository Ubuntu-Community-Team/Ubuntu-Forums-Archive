---
title: "Best idea to share a partition between Windows and Ubuntu"
date: 2006-01-15
forum: Desktop Environments
---

### Post by cadumg on 2006-01-15
I've just moved from Windows to Ubuntu, however, I know that I have to read/write in many files that I have in my documents partition using both Windows and Ubuntu.... What is the best way to read/write in both ?

I've heard that write in NTFS using Ubuntu is not safe... by the way FAT32 is not as good as NTFS... I heard about using [http://www.fs-driver.org/](http://www.fs-driver.org/) to read ext3 in windows, but it is not fast...

Any suggestion/idea ?

thanks a lot!

---

### Post by greenway on 2006-01-15
As far as I know, reading NTFS partitions in Linux is still not supported and I never heard about reading ext3 partitions under Windoze. I use fat32 myself for this purpose and it works good enough.

-mattijs

---

### Post by byen on 2006-01-15
I have been using Linux for a while now and I can pretty much say that though there are many work-arounds that explain how to get write permissions on NTFS ... It is hightly unstable and might lead to data corruption. The best thing to do would be to have a shared FAT drive. This way you would have write access to that drive from Windows as well as Linux.
Hope that helps. Goodluck.

---

### Post by Invictre on 2006-01-15
i was just looking around and i read something about people new to ubuntu. i found this link: [http://users.bigpond.net.au/hermanzone/]("http://users.bigpond.net.au/hermanzone/").

---

### Post by dgermann on 2006-01-15
cadumg--

Not sure how you want to access these files. The idea for dual boot works if they are all on one machine; if they are on a network, you might look into Samba. [http://us2.samba.org/samba/]("http://us2.samba.org/samba/")

---

### Post by shade11 on 2006-01-15
I use the ext3 format for my Ubuntu Breezy Partition, and the NFTS format for my Windows Partition. They work great and I think this would be a good idea.

---

### Post by skirkpatrick on 2006-01-15
I have a small FAT32 partition for files that both OS's share and have installed [http://uranus.it.swin.edu.au/~jn/linux/ext2ifs.htm](http://uranus.it.swin.edu.au/~jn/linux/ext2ifs.htm) on Windows.

---

### Post by briancurtin on 2006-01-16
[QUOTE=shade11]I use the ext3 format for my Ubuntu Breezy Partition, and the NFTS format for my Windows Partition. They work great and I think this would be a good idea.[/QUOTE]
yeah but OP is looking to write to his windows partition

---

### Post by Herman on 2006-01-16
cacmg,
> I've just moved from Windows to Ubuntu, however, I know that I have to read/write in many files that I have in my documents partition using both Windows and Ubuntu.... What is the best way to read/write in both ?

I've heard that write in NTFS using Ubuntu is not safe... by the way FAT32 is not as good as NTFS... If you have not already installed ,in my opinion FAT32 is the best for WIndows if you are planning to dual boot with Linux. I have read that NTFS is slightly better for Windows from a security point of view. If you are dual booting with Ubuntu, why not use Ubuntu for all your internet and e-mail work and refrain from connecting to the interent with Windows at all? That way you will not be bothered with any spyware or viruses. Therefore, if you don't use Windows on the internet, then it is not important to have NTFS,as there will be no security issues in Windows to worry you. If you can use your computer that way, then FAT32 is better since it can be both read and written to by Ubuntu.
However, not everyone will find it convenient to do things this way, and if you already have Windows installed with NTFS, I have read that you can't change back easily.

The next best thing to do is to make yourself a seperate FAT32 partition which both systems can read and write to. 
The easiest way to make one of those would be to try out the brand new 'GParted Live CD-0.1' (partitioning software) It is free and only a 34 MB download. The first stable version just was released a few days ago and I am trying it out right now, it's amazing! If you can download this .iso file, and burn it to a CD you should find it very useful. You should easly be able use GParted on that live CD to resize either your Ubuntu or your Windows partition and make a new FAT32 partition somewhere on your disk. (It does not have to be in the middle for both operating systems to 'see' it, it can be anywhere), but you might need to edit /etc/fstab for Ubuntu to recognise it. A good idea might be to make it beside your swap area since very often your swap will be automatically created as a logical partition and logical partitions belong together. Otherwise can make it a primary partition and put it anywhere, if you only have two other primaries made already. See my second signature link for GParted livecd-0.1 ,I hope this helps you, (Herman) :D

---

### Post by Thirsteh on 2006-01-16
Do FAT32.

---

### Post by newuser111 on 2006-01-16
make a fat32 partition to share files between windows and linux or you could try captive ntfs, which is the utility that lets you write to ntfs partitions, some say its safe, some say its risky, ive never tried it so i cant comment

[http://www.jankratochvil.net/project/captive/](http://www.jankratochvil.net/project/captive/)

---

