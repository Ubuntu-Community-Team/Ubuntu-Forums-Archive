---
title: "Pulling my hair out because no one is helping me and IRC won't work. Some assistance?"
date: 2008-01-07
forum: Dell  Ubuntu Support
---

### Post by Mnemonica on 2008-01-07
I'm getting GRUB error 17.

I do not get a boot menu. I do not get a prompt. I only get "grub1_5 error 17" in white text with a black background. If I press any buttons, my computer beeps at me mockingly. If I hold ctrl+alt+delete the computer restarts and then shits on me with the same thing anyway. 

When I boot from the Live CD and follow [this]("http://ubuntuforums.org/showthread.php?t=224351")

It gives me this series of errors:

"find /boot/grub/stage1" returns "Error 15: File not found"

I can do "root (hd0,1)" or whatever I want without getting an error... But when I issue the next command (regardless of whether I'm in (hd0,0) or (hd9,9)... Yes, I have tried them all even though I only have one hard-drive with three partitions)

"setup (hd0)"  (Or hd[whatever]) I get error 17 again.

gparted doesn't see any partitions if I go to edit them.

But when I issue "sudo fdisk -l" in terminal, I get this:

```
ubuntu@ubuntu:~$ sudo fdisk -l
Warning: invalid flag 0x0000 of partition table 5 will be corrected by w(rite)

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa0000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           4       32098+  de  Dell Utility
/dev/sda2               5        1310    10485760    7  HPFS/NTFS
/dev/sda3   *        1310       11722    83632128    7  HPFS/NTFS
/dev/sda4           11723       14594    23062332+   f  W95 Ext'd (LBA)
```


I'm at a complete loss. The reason for the title of this post is because I've been to at least five other forums, and I've gotten ONE reply over the course of two days. I've read as much as I can, and nothing works.

I believe that the issue I am having has been well articulated, and I know that I'm not any more important than anyone else... But please, don't just post a random thought about this and then never come back to see if I've given you a response (as seems the norm). I would go to IRC, but for some reason I can't seem to connect anywhere.

I just want to get my computer back. ANY and ALL help is greatly appreciated. I'll be on all night. I'm begging you, please help me trouble shoot this thing.

---

### Post by spivak.d on 2008-01-07
I understand your frustration. I have limited GRUB reinstalling experience, but I'll try to help.

So just a more obvious question.. are you sure it's not the install media that's bad? Have you run the test to verify its contents as complete?

---

### Post by chewearn on 2008-01-07
Looking at your fdisk output, it looks like there in no ubuntu or linux installed.

Can you identify the contents of the various partitions?

> 
/dev/sda1               1           4       32098+  de  Dell Utility
/dev/sda2               5        1310    10485760    7  HPFS/NTFS
/dev/sda3   *        1310       11722    83632128    7  HPFS/NTFS
/dev/sda4           11723       14594    23062332+   f  W95 Ext'd (LBA)
sda1 looks like Dell recovery partition
sda2 some Windows (NTFS) partition
sda3 looks like Windows root partition (got boot flag)
sda4 FAT32?  Data partition?

---

### Post by Mnemonica on 2008-01-07
Thanks very much.

I've been using my computer in it's dual-boot condition for almost half a year (between Vista and Ubuntu). Never had a problem this extreme.

There should be a Recovery Partition (for Vista), Vista, Ubuntu, and the swap partition for Ubuntu.

---

### Post by Mnemonica on 2008-01-07
I know that the one with the boot flag is my Vista partition... The one above that -should- be the Ubuntu Safe Mode thing... And the Top one is Ubuntu.

The bottom one is the recovery?

I know the first three for a fact, though.

EDIT: Or at least that's how it should be... The fact that the top one says "Dell Utility Partition" leads me to believe that there is something more screwed up...

---

### Post by chewearn on 2008-01-07
> **Mnemonica said:**
> I know that the one with the boot flag is my Vista partition... The one above that -should- be the Ubuntu Safe Mode thing... And the Top one is Ubuntu.

The bottom one is the recovery?

I know the first three for a fact, though.

EDIT: Or at least that's how it should be... The fact that the top one says "Dell Utility Partition" leads me to believe that there is something more screwed up...

Something definitely screwed up with your partition table; the partition lists reported by fdisk does not match your real harddisk content at all.

I really don't know how to fix that, without causing more damage, or reformat.

---

### Post by Mnemonica on 2008-01-07
So, essentially, the only solution is formatting the drive and starting over?

Do you have ANY idea as to what could have caused something like this? So far it seems like a completely irrecoverable error... Not the GRUB error, exactly, but the whole issue. I didn't change *anything* the last time I was on... I booted into Vista, checked my email, and powered down... That was it. Turn it on the next day, and this. Pretty ridiculous.

If you don't have any idea, do you know someone that might?

---

### Post by chewearn on 2008-01-07
> **Mnemonica said:**
> So, essentially, the only solution is formatting the drive and starting over?

Do you have ANY idea as to what could have caused something like this? So far it seems like a completely irrecoverable error... Not the GRUB error, exactly, but the whole issue. I didn't change *anything* the last time I was on... I booted into Vista, checked my email, and powered down... That was it. Turn it on the next day, and this. Pretty ridiculous.

If you don't have any idea, do you know someone that might?

There are software tools that might be able to repair/recover your partitions.  Unfortunately, I have never used any, so I'm not able to recommend.

Your harddisk itself could be crashing.  If the data on your drive is really important, you might want to seek professional data recovery help.

If you know the harddisk model/manufacturer, you might be able to find iso image of a harddisk diagnostic in their website; e.g. Maxtor used to have a bootdisk called PowerMax, which can perform physical diagnostic of their harddisk.  But of course, Maxtor is no more (bought over by Seagate).

Bear in mind, the harddisk diagnostic might not preserve your existing data; so only do this after you have recovered your data.

---

### Post by Mnemonica on 2008-01-07
Alright, I've been searching around, but no luck as of yet. I know that it's an SATA drive and that it's a Dell computer... *shrug* Other than that I'm really not sure. I'll ask around locally and see if I can find someone that can get some important stuff off of the Vista side of it. 

Thanks very much for the help. Even if it didn't really improve the situation, it's nice to know that I did everything that I could.

---

### Post by njparton on 2008-01-07
Try the gparted live cd from sourceforge.  From that you can delete only the partitions you believe to have issues with and leave your windows partitions alone.

---

### Post by Mnemonica on 2008-01-07
@ njparton: Alright, downloading it now. I'll post soon and let you know how it went...

---

### Post by johnw2007 on 2008-01-07
From the fdisk printout it looks as though you have somehow lost your linux partitions. If that is the case you need to be able to boot into Vista to recover your Windows data. To do this you need to use fixmbr to er.. fix the mbr to get a Windows boot. Try the instructions at [http://support.microsoft.com/kb/927392/en-us]("http://support.microsoft.com/kb/927392/en-us")

---

### Post by Mnemonica on 2008-01-07
Holy Hell it did something!!! I went to the "Boot partition #1 on first hard drive" option and it worked. I got into the Dell Utility Partition.

The Second partition returned: BOOTMGR is missing

I had to use ctrl+alt+del to restart

The Third partition got me into Vista!!! I never thought I'd be happy to see Vista, ever... But I was when that started up. Everything in Vista appears to be fine. Slow and bulky as usual, but wireless works. I'll transfer my important information after I check out whats on the fourth partition (unless fourth is ubuntu).

Alright... Fourth one returned an actual error. 

```
Error 13: Invalid or unsupported executable format

Press any key to continue...
```

I hit enter and it returns me to the gparted live menu, but its all scratchy looking and impossible to read. But I can tell that the menu works because I can scroll up and down with the arrow keys. I restarted the computer.

I'm going to be working in Vista now, getting all of my important stuff off of there, thank God. So now if it comes down to me having to format, I'll be pissed, but ok with it. :)

Thanks again nj, this really saved my ***.

Anyone else have any ideas about the messed up partitions?

---

### Post by saru411 on 2008-01-07
whenever grub decides to crap out on me i use my installation cd. i start the installation process but dont format any of the drive(very easy to do if you use the alt cd and when partitioning look to make sure you have all of the partitions to use existing data/do not format!) from there i follow the installation process so that it reinstalls grub. installation fails a little further down the installation process. from there just back out of the installation and restart. this is the simpliest way ive run into to solve grub issues. if you need other options this is the thread i found this answer in and it also lists other options([http://ubuntuforums.org/showthread.php?t=24113&highlight=blue+grub](http://ubuntuforums.org/showthread.php?t=24113&highlight=blue+grub))
hope this helps :)

---

