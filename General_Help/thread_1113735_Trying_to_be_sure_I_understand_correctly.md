---
title: "Trying to be sure I understand correctly"
date: 2009-04-01
forum: General Help
---

### Post by wanderingarticfox on 2009-04-01
I've been doing a lot of reading via the main site as well as the forums and also at Wiki. I think I've almost got my game plan laid out for my new build but I need some input on where and how my thinking and planning might not be correct.
I'll intially do a clean instal of XP-Pro 32 bit, chkdisc, defrag then do my Ubuntu instal with the advanced method utilizing GRUB. I will most likely 50/50 the HDD of either 500,640 or 750GB and be using SATA 3.0 off a Gigabyte GA-MA790GP-UD4H board.
Later on [several months] I will resize partitions and instal Window 7 32 bit  once again using the GRUB not MS MBR.
This is where I'm really not sure about my thinking; if I want to add an internal HDD for more storage and I want to use it for storage for Ubuntu can I boot into Ubuntu and format and label that drive and then when working with windows the MS MBR ignore or not see that or not try and plug-n-play that drive?
Also, the inverse would be to add another internal HDD and boot Windows and format and label for use as extra storage for the MS OS's?
I'm just not real clear. I don't need RAID, or if I did it would just be JBOD which if I understand correctly is what these new SATA II firmware controlers on the motherboard are doing kinda.

---

### Post by buminatrain on 2009-04-02
windows wont be able to see anything formatted in ext3 or ext4 so it will just ignore it.

---

### Post by mocoloco on 2009-04-02
FYI, after a fresh XP install I don't think you need to chkdsk or defrag. :)
For the storage thing, it depends on what your main use will be.  The most neutral filesystem would be Fat32, both OSes would be able to read and write to it fine.  If you'll have files with different permissions or need other Unix-like features then you can go with ext3, and there actually is a driver for MSWin that will let it see ext3 partitions.  It's called [ext2ifs]("http://www.fs-driver.org/") (as the name implies it's ext2, but this works with ext3 fine, there's a [detailed explanation]("http://www.fs-driver.org/faq.html#acc_ext3") on their site about this).
If you want Windows support for big files or maybe you'd use the drive on other Windows systems then you could go with NTFS, Linux will be able to read and write to it also, but again won't have all the unixy goodness.

---

### Post by Yashiro on 2009-04-02
> FYI, after a fresh XP install I don't think you need to chkdsk or defrag. You do. In Vista you can get away with not bothering.

---

### Post by wanderingarticfox on 2009-04-02
Boy oh boy have I just spiked my learning curve. Thanks for info and links.

---

### Post by wanderingarticfox on 2009-04-11
I missed the Boat on first try, see 'Boyo do I need help' thread posted 4-11-09

---

### Post by defaultusername on 2009-04-11
wanderingarticfox,

When I'm installing Windows, I always partition the disk to accomodate the operating system/swap (and thus the eventuality of reinstalling/upgrading) and then choose a second, larger partition for storage. My only Windows laptop utilizes the default partitioning scheme (C drive/swap), but then again it has a 60gB hard drive.

Just a bit of input.

---

