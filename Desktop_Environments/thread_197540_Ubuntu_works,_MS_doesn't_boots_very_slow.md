---
title: "Ubuntu works, MS doesn't boots very slow"
date: 2006-06-15
forum: Desktop Environments
---

### Post by mmmpancakes on 2006-06-15
I successfully installed Ubuntu on a partition so it can dual boot with Windows Vista. However, when I boot into Windows, it takes at least 30 minutes for windows to load. It sticks on the loading screen, with the wavy bar. The wavy bar keeps in motion, but so far (20 minutes later) Windows has yet to load. Ubuntu loads fine when I boot into it. ANy suggestions?

Thanks in advance.

---

### Post by PhoenixP3K on 2006-06-15
Thats weird... considering most Ubuntu installs can't detect Vista to add it on the GRUB menu... 

In your case it's hard to tell with little detail on your hardware and the way you partitionned your drive. Vista should be on NTFS, but then again where did Ubuntu install it's SWAP, Linux ext2 and ext3 partitions is a mystery :p

Seriously, Vista being beta and them developping a totally new boot loader (on Vista's end), it's hard to elaborate on the problem. I just gave my 2¢, someone else might of experienced the same situatiion and might be able to help you out. Good luck ;)

---

### Post by mmmpancakes on 2006-06-15
My biggest fear is that there's a swap memory issue. Since I can safely boot into Ubuntu, is there a way from there I can tweak the partitions?

---

### Post by frup on 2006-06-15
do you have a partitioned disk or 2 seperate HDDs?
personally i would have them on 2 different disks if possible and manually choose which one loads by plugging it in master..

---

### Post by mmmpancakes on 2006-06-15
[QUOTE=frup]do you have a partitioned disk or 2 seperate HDDs?
personally i would have them on 2 different disks if possible and manually choose which one loads by plugging it in master..[/QUOTE]

It's a partitioned single disk. Here's what the disk manager in Ubuntu is showing:

partition 1: Windows virtual fat 31.35 mb
partition 2: Windows NTFS 129,81 gb with 92.29 free
Free Space: 16.7 gb
Partition 3: 2.77 GB (ubuntu partition, root)
Free Space: 23.53

EDIT: Partition 2 is the partition loaded with Vista

---

### Post by frup on 2006-06-15
did you load vista at all by itself? how was the performance comparison? does your machine meet its minimum requirements?

you cant choose which partition to load from through bios can you?

---

### Post by mmmpancakes on 2006-06-15
I had a dual boot with Ubuntu and XP. Grub got messed up after I installed Vista onto XP, so I re-installed Ubuntu so Grub would re-install (n00b, sorry). Now, Ubuntu runs fine. 

I get a boot screen that allows me to choose which OS to boot into. 

My system meets the min requirements (about 6 weeks old). VIsta was running fine until I re-installed Ubuntu. That's probably some info I should have put out first.

---

### Post by mmmpancakes on 2006-06-16
bump :D

---

### Post by jrd on 2006-06-16
I tri boot Vista, Kubuntu, and XP. Xp and Kubuntu boot up fast and perform well, Vista takes about 3x longer to boot than either of them, then the performance sucks once it does boot. I meet the requirements to run Vista too. I think it's just slow, maby because its just the beta version. I know if it doesn't inprove, a lot of people will not use it.

---

### Post by mmmpancakes on 2006-06-16
So at this point should I start preparing for the fact I need to reformat, and reinstall XP and Ubuntu? Vista loads slowly, but not this slowly (30 + minutes). I'm pretty sure I hosed the swap memory or didn't configure the partitions correctly (partition n00b). This is a user-error issue, I'm sure.

---

