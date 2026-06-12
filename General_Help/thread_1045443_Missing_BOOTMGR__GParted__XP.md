---
title: "Missing BOOTMGR / GParted / XP"
date: 2009-01-20
forum: General Help
---

### Post by dhtseany on 2009-01-20
Hi all,
First, I'm not really "new" to UB. I use it primarily for recovering lost data from customer PC's that they've generally toasted. 

OK, so here we go. I have a Dell Inspiron 6400 with a 20 gig recovery partition. The problem with most recovery processes is they don't format the drive first, potentially leaving alot of garbage on the drive. So I booted to my USB Jumpdrive with UB 8.10 installed on it. I used GParted to format the primary partition, then applied the changes. That's it. The next step was supposed to be reboot, hold down Ctrl+F11 then start the recovery process for XP Media Center Edition that came with the laptop. Instead, it seems I've screwed something up with the partition table and I don't understand how. All I did was reformat the main partition using NTFS and applied it. Now I get a message "Missing BOOTMGR. Press ALT+CTRL+DEL to restart".

How can I fix this? Simply formatting the whole drive isn't an option because my customer doesn't have the reinstall CD(s).

Any help would be super appreciated!

Thanks,
Sean

---

### Post by icanfly0307 on 2009-01-20
When do you get this error? After the BIOS screen? And when are you supposed to press Ctrl+F11 to access the recovery process?

---

### Post by cariboo on 2009-01-20
Most manufacurers that don't supply an install cd, put the recovery data on the first partition.

I would suggest using [testdisk]("http://www.cgsecurity.org/wiki/TestDisk"), to recover the data from the mistakenly formated partition. Testdisk is in the repositories.

Jim

---

### Post by dhtseany on 2009-01-20
Yeah, during Dell's POST screen. It's a hidden option. You're supposed to press Ctrl+F11 to start the process. And yes, it did work before but didn't format it so I opted to format it myself and do the process a second time. 

As far as testdisk goes, how do I use it?

Thanks,
Sean

---

### Post by icanfly0307 on 2009-01-20
Hang on. so you get this error when you press Ctrl+F11? What happens if you just leave the computer after the POST screen?

---

### Post by dhtseany on 2009-01-20
No, I get this error when the laptop attempts to boot from the hard drive, whether it be the Recovery Partition or the main partition. Either way it spits back that error.

Thanks,
Sean

---

### Post by dhtseany on 2009-01-20
Oh, BTW it's also worthy to note that the both partitions still mount just fine from UB and I have full read/write access to both as well.

Thanks,
Sean

---

### Post by caljohnsmith on 2009-01-20
Getting a "BOOTMGR missing" error means your computer is still trying to boot the Vista partition, which no longer has a bootmgr. If you can't manually use your Ctrl-F11 trick to start the recovery partition, you could instead transfer the boot flag from your Vista partition to the recovery partition, and then your BIOS will try to boot the recovery partition on start up. I think that would work, but how about first posting:
```
sudo fdisk -lu
```
And identify your partitions. We can work from there if you want.

---

### Post by icanfly0307 on 2009-01-20
> **caljohnsmith said:**
> Getting a "BOOTMGR missing" error means your computer is still trying to boot the Vista partition, which no longer has a bootmgr. If you can't manually use your Ctrl-F11 trick to start the recovery partition, you could instead transfer the boot flag from your Vista partition to the recovery partition, and then your BIOS will try to boot the recovery partition on start up. I think that would work, but how about first posting:
```
sudo fdisk -lu
```
And identify your partitions. We can work from there if you want.

Agreed. Caljohnsmith has made an excellent point. Each hard drive has exactly ***one*** partition with a "Boot" option. Vista used to have that flag before you formatted it so the hard drive now has **NO** bootable partition. I recommend that you download the GParted LiveCD and add a "Boot" flag to your recovery partition. That way, your hard drive will try to boot from it instead of Vista.

Hope this helps... :)

---

### Post by dhtseany on 2009-01-21
Hey guys, just to update I figured it out.

Thanks though,
Sean

---

### Post by theWrkncacnter on 2009-01-21
How did you figure it out? The world may never know!

---

### Post by icanfly0307 on 2009-01-21
Great to know you sorted it out. Please mark the thread as solved.

---

