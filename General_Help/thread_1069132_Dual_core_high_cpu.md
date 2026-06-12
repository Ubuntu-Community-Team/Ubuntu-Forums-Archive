---
title: "Dual core high cpu"
date: 2009-02-13
forum: General Help
---

### Post by Robbyx on 2009-02-13
Core 2 is running at 100%. Htop shows that 89% of the cpu is being run by 

sbin/mount.ntfs /dev/sdb1 /media/mydocs -0 rw, nosuid,nodev, user, nls=ttf8,unmask=007

I  sdb1 is the rade drive. How can I change the settings so that the cpu is not running at 100%? I haven't had a crash so it should not be synchronisation of the two drives.



Robin

---

### Post by Slim Odds on 2009-02-13
> **Robbyx said:**
> sbin/mount.ntfs /dev/sdb1 /media/mydocs -0 rw, nosuid,nodev, user, nls=ttf8,unmask=007

I  sdb1 is the rade drive. How can I change the settings so that the cpu is not running at 100%? I haven't had a crash so it should not be synchronisation of the two drives.


A RAID drive should be something like /dev/md0

---

### Post by Robbyx on 2009-02-13
Actually in my case sdb1 is the rade drive.

What do think is causing the high cpu? Currently both cores are now at 74%

---

### Post by Slim Odds on 2009-02-13
> **Robbyx said:**
> Actually in my case sdb1 is the rade drive.

What do think is causing the high cpu? Currently both cores are now at 74%

What is a "rade" drive?

sdb1 may be one of the drives that you are using within your RAID array, but a mountable RAID array is /dev/md?

[http://www.howtoforge.com/install-ubuntu-with-software-raid-10](http://www.howtoforge.com/install-ubuntu-with-software-raid-10)

---

### Post by fjgaude on 2009-02-13
The raid array is formatted to NTFS?

Is the raid created in your BIOS?

Do you understand what **dmraid** is?

Can you show us the results of:

```
sudo fdisk -l
```

Thanks.

---

### Post by Robbyx on 2009-02-14
> **fjgaude said:**
> The raid array is formatted to NTFS?

Is the raid created in your BIOS?

Do you understand what **dmraid** is?

Can you show us the results of:

```
sudo fdisk -l
```

Thanks.

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00011035

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3725    29921031   83  Linux
/dev/sda2            3726        7647    31503465   83  Linux
/dev/sda3            7648       60057   420983325    5  Extended
/dev/sda4           60058       60801     5976180   82  Linux swap / Solaris
/dev/sda5            7648       12783    41254888+  83  Linux
/dev/sda6           12784       25547   102526798+  83  Linux
/dev/sda7           25548       60057   277201543+  83  Linux

Disk /dev/sdb: 250.0 GB, 250058301440 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00075fd0

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       30401   244196001    7  HPFS/NTFS

Disk /dev/sdc: 2055 MB, 2055208960 bytes
16 heads, 32 sectors/track, 7840 cylinders
Units = cylinders of 512 * 512 = 262144 bytes
Disk identifier: 0xa3aa5e04

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1        7840     2007024    e  W95 FAT16 (LBA)
rob@rob-desktop:~$ 


I have a raid card with two mirrored hard disk attached.

Robin

---

### Post by fjgaude on 2009-02-14
You're booting from sda1, and the two drives mirrored are sdb1 and sdc1, formatted to NTFS? No, only sdb1 is NTFS and sdc1 is W95, FAT16... I don't see anything that is an array.

How did you create the mirror array, please?

The raid card used a Windows program or the BIOS to setup the raid1? Please!

You can see the Windows drives using **dmraid**. You can download from the repository to get it:

```
sudo apt-get install dmraid
```

Read the man pages after you install. Hope this helps. Let us know how you are doing.

---

### Post by Robbyx on 2009-02-14
Currently the CPU% has dropped right back. 

HTOP shows 1 at 4% and core 2 at 1%

I had hopped that htop would indicate what was eating the resources but I can not see the cause.

The cpu ubuntu panel widget shows cpu on demand 2ghz (74%). I guess they are measuring different things. Presumable the maximum GHz that the cpu can run.



I became concerned about cpu usage because Firefox is often not allowing me to type without me having to wait for the cursor to reappear. It is as if the focus is lost and I have to wait for Ubuntu to cycle back to Firefox. So I thought something was taking memory over. However even at the low cpu usage shown by htop it is sometimes sticking when I type.

Robin

---

### Post by Robbyx on 2009-02-14
> **fjgaude said:**
> You're booting from sda1, and the two drives mirrored are sdb1 and sdc1, formatted to NTFS? No, only sdb1 is NTFS and sdc1 is W95, FAT16... I don't see anything that is an array.

How did you create the mirror array, please?

The raid card used a Windows program or the BIOS to setup the raid1? Please!

You can see the Windows drives using **dmraid**. You can download from the repository to get it:

```
sudo apt-get install dmraid
```


Read the man pages after you install. Hope this helps. Let us know how you are doing.


I am using the 3com raid card. So the array should not show up in fdisk. It is a hardware raid.
Robin

---

### Post by Slim Odds on 2009-02-14
> **Robbyx said:**
> I am using the 3com raid card. So the array should not show up in fdisk. It is a hardware raid.
Robin

Read up on "fakeraid". It's likely that your motherboard does not do "true" RAID.

I found that out on my Soyo mobo, although I'm not dual booting. So I went to software RAID and am very happy with it (RAID0 for performance).

This may or may not help: [https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

---

### Post by Robbyx on 2009-02-14
No. It is true raid, but what do you think is the cause of my high cpu usage.

---

### Post by fjgaude on 2009-02-15
> **Robbyx said:**
> No. It is true raid, but what do you think is the cause of my high cpu usage.

Since you don't have a Linux driver for the 3Com raid card Ubuntu doesn't recognize the array?

Still **dmraid** might permit you to mount the array.

---

### Post by Robbyx on 2009-02-15
> **fjgaude said:**
> Since you don't have a Linux driver for the 3Com raid card Ubuntu doesn't recognize the array?

Still **dmraid** might permit you to mount the array.

As I recall the driver is built into Ubuntu, but the correct name for the raid drive is 3ware 8006-2LP.

Robin

---

### Post by fjgaude on 2009-02-15
Okay, I think I'm beginning to understand your situation. Your raid array is not understood by **fdisk** because it doesn't understand raid, period.

You use this line to mount the array:

```
sbin/mount.ntfs /dev/sdb1 /media/mydocs -0 rw, nosuid,nodev, user, nls=ttf8,unmask=007
```

Instead try this and see what happens:

```
sudo mount -t ntfs /dev/sdb1 /media/mydocs
```

Let us know what happens, please.

---

### Post by Robbyx on 2009-02-15
> **fjgaude said:**
> Okay, I think I'm beginning to understand your situation. Your raid array is not understood by **fdisk** because it doesn't understand raid, period.

You use this line to mount the array:

```
sbin/mount.ntfs /dev/sdb1 /media/mydocs -0 rw, nosuid,nodev, user, nls=ttf8,unmask=007
```

Instead try this and see what happens:

```
sudo mount -t ntfs /dev/sdb1 /media/mydocs
```

Let us know what happens, please.

I am very muddled. When Ubuntu starts apart from presenting the bios set up screen it also presents a screen for the set up of the two mirrored raided drives. This has previously been set up and works in that once ubuntu is loaded I can see the media/mydocs drive from within the file managers. I am able to access the raid drive even though both are connected to the raid card via sata connections.
To me this shows that my particular raid drive is recognised by ubuntu (and that is why I bought it).

```
sudo mount -t ntfs /dev/sdb1 /media/mydocs
``` To me is unnecessary because the drive can be seen. Have I missed your point?

Robin

---

### Post by fjgaude on 2009-02-15
Gosh, I don't believe you have a raid array at all. Did you use the BIOS to setup two drives to be a raid?

You know it normally takes at least two drives or partitions to make an array, the simpliest.

Can you tell us what is going on with your computer? Who set up that command line to mount? The **mount** program is in /bin and not /sbin.

Please, anwers to all questions. Thank you.

---

### Post by Slim Odds on 2009-02-15
> **Robbyx said:**
> I am very muddled. When Ubuntu starts apart from presenting the bios set up screen it also presents a screen for the set up of the two mirrored raided drives. This has previously been set up and works in that once ubuntu is loaded I can see the media/mydocs drive from within the file managers. I am able to access the raid drive even though both are connected to the raid card via sata connections.
To me this shows that my particular raid drive is recognised by ubuntu (and that is why I bought it).

Well, not to be picky, but Ubuntu does not present the BIOS setup. The BIOS does that.

So now I'm wondering about "it also presents a screen for the set up of the two mirrored raided drives".

In the case of "true" RAID, the combining of the drives would be invisible to Ubuntu. In the case of these fakeRaid setups, Ubuntu can see both drives independently. I have a motherboard that works that way.

In my case, I'm not dual booting, so I just used a software RAID and it works great.

I think that you're going to have to give some more detailed information if you expect to get an answer.

---

### Post by Robbyx on 2009-02-16
> **fjgaude said:**
> Gosh, I don't believe you have a raid array at all. Did you use the BIOS to setup two drives to be a raid?

You know it normally takes at least two drives or partitions to make an array, the simpliest.

Can you tell us what is going on with your computer? Who set up that command line to mount? The **mount** program is in /bin and not /sbin.

Please, anwers to all questions. Thank you.

I did not use the Bios to set up the raid. It is not a software raid.

I have not used the mount command suggested because I have a working system which is showing the raid drive mounted. See fdisk output above.

Robin

---

### Post by Robbyx on 2009-02-16
> **Slim Odds said:**
> Well, not to be picky, but Ubuntu does not present the BIOS setup. The BIOS does that.

So now I'm wondering about "it also presents a screen for the set up of the two mirrored raided drives".

In the case of "true" RAID, the combining of the drives would be invisible to Ubuntu. In the case of these fakeRaid setups, Ubuntu can see both drives independently. I have a motherboard that works that way.

In my case, I'm not dual booting, so I just used a software RAID and it works great.

I think that you're going to have to give some more detailed information if you expect to get an answer.

Sorry I have not been concise. The raid setup screen is not part of Ubuntu. It is presented when I start up the computer.  I am definitely not using a fake raid.

Robin

---

### Post by fjgaude on 2009-02-16
I give up... sorry I can't help.

---

### Post by Robbyx on 2009-02-16
Thank you for trying. Much appreciated. I actually think the raid side is under control. My concern was the high cpu usage but currently this much lower so it may have been a background backup program. 

Robin

---

### Post by Slim Odds on 2009-02-16
> **Robbyx said:**
> Thank you for trying. Much appreciated. I actually think the raid side is under control. My concern was the high cpu usage but currently this much lower so it may have been a background backup program. 

Robin

The indexing of the tracker application often gets people concerned. It runs for a while doing it's job and then it's done.

Perhaps it was something like that.

---

