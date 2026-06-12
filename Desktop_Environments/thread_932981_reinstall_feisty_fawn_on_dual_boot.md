---
title: "reinstall feisty fawn on dual boot"
date: 2008-09-29
forum: Desktop Environments
---

### Post by jmp5167 on 2008-09-29
Needless to say I am new to using any linux.  I recently set up a dual boot config so I can get used to it and ease myself into the change.  After using it for a while I have successfully made a mess of it.  I was wondering how I could either reinstall ubuntu on its partitioned space or like restore to orginal settings.

---

### Post by lisati on 2008-09-29
If you have a "LiveCD" the reinstall option should be too difficult. It's a bit "brute force" but I've used it a few times myself without too many hassles. 

The approach I normally use is to boot up the Live CD, use the copy of gparted on the disk (it's on the System->Administration menu) to delete the messed up Ubuntu partition (you might have to unmount it first). Then I'd run the install process, telling it to use the "Guided, use largest free contiguous free space" option.

Good luck.

---

### Post by jmp5167 on 2008-09-29
thank you for helping but Ive hit another little snag.  I have 6 divisions that pop up in the GParted window.
/dev/sda1 ntfs                    57.74GiB
/dev/sda4 exteneded               39.11GiB
---/dev/sda5 ext3                 37.47GiB
---/dev/sda6 linux-swap           1.65GiB
/dev/sda2 fat32                   13.92GiB
/dev/sda3 ntfs                    1.00GiB

the bar that contains the 'picture' is over half /dev/sda1  then /dev/sda5
and then /dev/sda2.

I don't no if this is correct but what I understand is that /dev/sda1 is my windows partition.  /dev/sda is my linux partion.  Im guessing /dev/sda2 is my reboot that came pre-loaded on my computer.  Would I be correct in just deleting the /dev/sda4.. or should i only delete my /dev/sda5?

---

### Post by lisati on 2008-09-29
> **jmp5167 said:**
> thank you for helping but Ive hit another little snag.  I have 6 divisions that pop up in the GParted window.
/dev/sda1 ntfs                    57.74GiB
/dev/sda4 exteneded               39.11GiB
---/dev/sda5 ext3                 37.47GiB
---/dev/sda6 linux-swap           1.65GiB
/dev/sda2 fat32                   13.92GiB
/dev/sda3 ntfs                    1.00GiB

the bar that contains the 'picture' is over half /dev/sda1  then /dev/sda5
and then /dev/sda2.

I don't no if this is correct but what I understand is that /dev/sda1 is my windows partition.  /dev/sda is my linux partion.  Im guessing /dev/sda2 is my reboot that came pre-loaded on my computer.  Would I be correct in just deleting the /dev/sda4.. or should i only delete my /dev/sda5?

The partition with your copy of Ubuntu is likely to be /dev/sda/sda5


This is how I understand what's on your system:

/dev/sda1 - Windows
/dev/sda2 - Data?
/dev/sda3 - Windows?
/dev/sda4 - Space for the following partitions
/dev/sda5 - Ubuntu - safe to delete if you are reinstalling Ubuntu from scratch (backup your data first!)
/dev/sda6 - used by Ubuntu - keep if you want to use the Live CD to reinstall

My dinner has just been served, maybe someone else will be able to offer some suggestions.

---

### Post by Sef on 2008-09-29
>                                   **reinstall feisty fawn on dual boot**             
             I would download Hard Heron as Fiesty's support will run out in 4 weeks, After that, no more update of any kind.

---

### Post by jmp5167 on 2008-09-29
> **Sef said:**
> I would download Hard Heron as Fiesty's support will run out in 4 weeks, After that, no more update of any kind.

I actually meant hardy heron, as you can see I am so new these names kind of sound the same.  When I tried to delete that partition an error came up that said I had to unmount it.  What does that mean and how do I do it

---

