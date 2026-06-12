---
title: "resize of partition doesnt work"
date: 2006-04-15
forum: Desktop Environments
---

### Post by gtfan1 on 2006-04-15
i have tried to do a dual boot on my laptop, running ubuntu and xp, but when i try to make a second partition on my hard drive using the ubuntu partitioner, it wont let me.  it says that it requires me to format at least 75% of the hard drive to complete the process.  is there a way i can use the 20 percent i have left on my 60 gig hard drive without disturbing my xp files(unfortunately i'm not completely ready to switch completely to ubuntu, but i'm hating windows more and more as time goes on!!!!)

---

### Post by aysiu on 2006-04-15
I know downloading another distro may seem excessive, but I've never had partitioning problems with [DiskDrake](http://www.ubuntuforums.org/showthread.php?t=114142).

---

### Post by gtfan1 on 2006-04-15
ok, thanks for the tip, i'll let ya know if it works out fine or not

---

### Post by gtfan1 on 2006-04-15
ok i tried doing what you suggested, and it didnt work either

---

### Post by aysiu on 2006-04-15
[QUOTE=gtfan1]ok i tried doing what you suggested, and it didnt work either[/QUOTE] What happened? Was there any kind of error? At what point?

If DiskDrake failed, I would imagine either you need to defragment the drive first, there are bad superblocks or some kind of corrupted part of your hard drive, or your hardware has failed somehow.

---

### Post by gtfan1 on 2006-04-15
i just figured it out, i was able to create another partition.  i created a fat32 system with 15 gig of space

i then exited out and tried to instal ubuntu again, but it wouldnt let me instal the os on the partition, it kept wanting me to format that partition, but wouldnt let me

---

### Post by aysiu on 2006-04-15
[QUOTE=gtfan1]i just figured it out, i was able to create another partition.  i created a fat32 system with 15 gig of space

i then exited out and tried to instal ubuntu again, but it wouldnt let me instal the os on the partition, it kept wanting me to format that partition, but wouldnt let me[/QUOTE] You're trying to install Ubuntu on a FAT32 partition?

---

### Post by gtfan1 on 2006-04-15
yes, because one of the guides i was reading about dual booting said to instal it on a fat32 partition

---

### Post by aysiu on 2006-04-15
[QUOTE=gtfan1]yes, because one of the guides i was reading about dual booting said to instal it on a fat32 partition[/QUOTE] Can you post that guide?

I don't know any guide that tells you to install Ubuntu to FAT32.

Some guides, like this one, will suggest you create a separate FAT32 partition to share data between Ubuntu and Windows XP:
[http://users.bigpond.net.au/hermanzone](http://users.bigpond.net.au/hermanzone)

But, as far as I know, you can't (and it isn't a good idea to) install Ubuntu on to a FAT32 partition. Your Ubuntu partition should be formatted as Ext3 (which the installer can do).

---

### Post by gtfan1 on 2006-04-15
so should go back and use diskdrake and change the fat32 partition to Ext3?

---

### Post by aysiu on 2006-04-15
[QUOTE=gtfan1]so should go back and use diskdrake and change the fat32 partition to Ext3?[/QUOTE] No, you can use the Ubuntu installer to format the partition as Ext3.

When you get to the part where you're asked to Erase the entire hard drive or Manually edit the partition table, choose to manually edit the partition table.

Press Enter on the currently FAT32 partition. 
Press Enter on **Use as:** and select **Ext3**
Press Enter on **Mount point** and select **/** (that's right--it's a forward slash)
Press Enter on **Format** and select **Yes, format it**.

---

### Post by gtfan1 on 2006-04-15
ok, that worked great, thank you.

---

### Post by aysiu on 2006-04-15
[QUOTE=gtfan1]ok, that worked great, thank you.[/QUOTE] Phew. I was getting worried.

---

