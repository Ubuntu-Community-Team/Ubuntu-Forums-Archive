---
title: "Windows for the chop"
date: 2006-07-21
forum: Desktop Environments
---

### Post by ColinG on 2006-07-21
Well, I think Dapper had done what I thought was impossible - it can do anything that I currently do on windows (and probably lots more). So, "Old XP Bill" is for the chop. The question is how do I use the disc space and comments guidance on the belopw options would be appreciated.

1) Can I format the drive from within Ubuntu and use the space as Home and if I do what about the current home partition?

2) Can I format the drive from within Ubuntu and then use it for playing with/testing Edgy?

Many thanks
Colin

---

### Post by Tamihania on 2006-07-21
Hi Colin,

Ad 1) Yes, you can do this - I strongly recommend you to read the pages by aysiu (the member of the Forum :) )  before you will start. The pages are as follows:
[Partitioning]("http://www.psychocats.net/ubuntu/partitioning.html")

[Separate home]("http://www.psychocats.net/ubuntu/separatehome.html")

[PartImage]("http://www.psychocats.net/ubuntu/partimage.html")

I would also recommend you to use QtParted or GParted (too create new partitions) - both available in repositories.

Ad 2) The answer is - probably yes - but I did not try it yet and can't share my own experience. Many persons here run different distro' es though, so I assume you can install Edgy on a separate partition (assuming you have enough space :) )

Good luck,

tami

---

### Post by ColinG on 2006-07-22
Thanks for this. What I have is windows xp on a seperate drive c (sda1). I would like to reformat that drive as ext2 (I think that is right) and then make that my home partition or perhaps a data holding partition.

I believe I can do that by using the Ubuntu onboard partitioner and then mounting the new partition via fstab. Am I correct and will it do any damage to the bootloader which is on the windows mbr?

Thanks a mil :) 
Colin

---

### Post by cptnapalm on 2006-07-22
ext2 can be made into ext3, which is the same thing but with journalling (which is a Good Thing).  If you have different things you might like to do with the drive, I'd suggest looking into the LVM stuff (which I know little about) as it can resize different partitions depending on need.

As far as making a /home partion, just mount the new partition on /mnt and copy everything from the home folder over.  Make sure its all there, then wipe out everything under /home.  Unmount /mnt and then remount it as /home.  Need to add the line to fstab too, of course.  (Why isn't there yet a handy dandy gui for some of this stuff, I don't know.)

The bootloader ought not be affected as it is not part of the main partioning scheme.  But running grub-install or lilo, depending, might not be a bad idea just to be on the safe side after all else is done.

---

### Post by jISh on 2006-07-22
If you want to test Egdy, I'd suggest looking up VMWare. It lets you install operating systems into a single file, which is treated as a hard drive by the OS. Much safer and easier than multiple-booting several OSes.

---

### Post by ColinG on 2006-07-22
Many, many thanks to all.

I'll give it my best shot 

Colin :D

---

### Post by ColinG on 2006-07-25
Well, I've deleted my windows partition on device sda1 and have reformatted as ext3. I've decided to use it solely as a data/back-up disc so have named it "Data". I now need to mount this in read/write mode at boot but am unsure of the fstab syntax.

Actually I have no idea at all really :-k but as a starter, would the below work?

/dev/sda1 /Data ext3 nodev,nosuid 0 2

Many thanks
Colin

PS I've created a directory /mnt/Data

---

### Post by ColinG on 2006-07-25
Think I've solved it. I used the following and now have RW access as user.

/dev/sda1   /mnt/Data   ext3   defaults   0   1

:D

---

