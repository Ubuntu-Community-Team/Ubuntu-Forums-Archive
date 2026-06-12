---
title: "Super Grub Disk"
date: 2009-02-15
forum: General Help
---

### Post by Nukinfuts on 2009-02-15
Long story short i need to install SGD to a pendrive (usb). I followed the instructions exactly, and i am getting the error 18 about the cylinder exceeding bios or some crap.

So according to the SGD wiki that means it needed to be formatted and partitioned with a ext3 or fat32 partition of 300mb, located at the beginning of the drive. 

I have done all this, multiple times, and the errors continue. I just need a way to fix/install grub from a pendrive, why is this so complicated? What a headache.

And please dont suggest i use a disk, i need this to work on the pendrive.

Any ideas?

---

### Post by Nukinfuts on 2009-02-16
Bump, i cannot find my answer anywhere. I miss my Ubuntu CD. The drive is dead in this computer so i used Wubi, and now im moving it to its own via lvpm. Which all went fine but grub count mount the partition now....ugh.

---

### Post by Nukinfuts on 2009-02-16
I'm an idiot. I was using sdc1 instead of sdc. So i got it installed to the usb key, and the computer is set to boot from it. But no matter which of the 3 usb ports i use all i get is a blinking cursor...

---

### Post by zwygart on 2009-02-16
I have SGD on my USB key. So it is possible. I had searched some time.

Why are you saying sdc? I install grub with a grub shell. It is easier. 

root (hdX,Y)
setup (hdX,Y)

It worked for me with Y of setup = 3, Even if I don't had a 4 primar partition. Don't ask me why it worked. So you may try different numbers, and without. Don't try the X with all the possible values. 

For more indication wich I may miss, enter my name in the advanced search on the right side.

---

### Post by Nukinfuts on 2009-02-18
sdc is my usb key.

I took this over to SGD forums, there is some more information there. If you guys wouldnt mind taking a peek you can post here or there and i will see it. I'm pulling my hair out...

[http://www.supergrubdisk.org/forum/index.php?topic=257.0](http://www.supergrubdisk.org/forum/index.php?topic=257.0)

---

### Post by zwygart on 2009-02-19
May be you have to format your stick. I had to. Type fdisk -lu. It should give some indications. If it says that you don't have a valid partition table, then the problem is this. Delete all partitions and make a correct partition table.

---

### Post by Nukinfuts on 2009-02-19
I have repartitioned/formatted it several times using both Fat32 and ext3. I even tried FAT16. Used ubuntu twice and Acronis in vista a handful of times.

---

