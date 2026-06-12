---
title: "Main C: Drive"
date: 2009-03-29
forum: General Help
---

### Post by DigitalNoise on 2009-03-29
Ok, I've successfully installed Ubuntu on my secondary SATA drive, and I'm able to dual-boot between Windows XP SP2 and Ubuntu just fine.

The issue I'm having is somewhat weird, though - I can't see anything on my "main" C: drive.  The HDD that Ubuntu is installed on has NTFS partions, and I can see those just fine.  An external HDD has both NTFS and FAT32 partions - Ubuntu sees those just fine.

But it does not see - or I can't find it - my main HDD with all of my Windows files on it.  Specifically there are programs on there that I want to try to run with Wine - but if I can't see them when browsing the system...

Any ideas?  Or am I missing something obvious?

---

### Post by DigitalNoise on 2009-03-29
I think I see the issue, I'm just not sure how to correct it:

There is no /dev/sda listed in either my /etc/fstab or /etc/mtab files - thus I don't think the primary SATA drive is being mounted.

My question is - if I just edit one of these files and add the appropriate line:```
/dev/sda0 /media/XP fuseblk rw,nosuid,nodev,allow_other,blksize=4096 0 0
``` will it actually mount and allow me to access the drive?

Btw - I took the settings from another NTFS drive that Ubuntu is mounting automatically - I figure it should work, but please correct me if I'm wrong.  Also I'm assuming /dev/sda0 is correct - when installing Ubuntu sda was listed as the 250GB SATA drive, which is the one I can't get to at the moment, and since there is just one big partition on that drive, I'm guessing that 0 is correct as well.

---

### Post by linorics on 2009-03-29
Make sure that you NTFS file system isn't locked. When you are in windows make you let windows shutdown completely via Start>Shutdown>Ok.

---

### Post by DigitalNoise on 2009-03-29
> **linorics said:**
> Make sure that you NTFS file system isn't locked. When you are in windows make you let windows shutdown completely via Start>Shutdown>Ok.
Hmnmm, I would've thought that the cold reboot to boot from the Ubuntu install CD would've had the same effect; but I guess I can reboot back into Windows and then shutdown and go back into Ubuntu

---

### Post by DigitalNoise on 2009-03-30
> **DigitalNoise said:**
> Hmnmm, I would've thought that the cold reboot to boot from the Ubuntu install CD would've had the same effect; but I guess I can reboot back into Windows and then shutdown and go back into Ubuntu
Well, a complete shutdown from Windows and then a cold boot directly into Ubuntu still has the same result - no main SATA drive available.

I took a look in the /dev folder and I see a sda listed in there - but it's not mapped in my mtab or fstab...

---

### Post by DigitalNoise on 2009-03-30
I've done some more digging, and through trial and error (including realizing I had to create the directory in /media that I wanted to mount to...), I came up with the following - and then got the error message below it:
```
:~$ sudo mount -t fuseblk /dev/sda /media/xp
mount: wrong fs type, bad option, bad superblock on /dev/sda,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```
Everything that I can determine tells me that /dev/sda is my primary Windows drive - and Windows boots up just fine from it - I was on for a couple of hours playing WoW earlier; so I know there's not an issue with the drive itself.

I did as suggested and ran:
```
:~$ dmesg | tail
[   43.940018] eth0: no IPv6 routers present
[   66.766670] UDF-fs: No VRS found         
[   66.796181] ISO 9660 Extensions: Microsoft Joliet Level 3
[   66.836313] ISO 9660 Extensions: RRIP_1991A              
[  135.475750] ppdev0: registered pardevice                 
[  135.525593] ppdev0: unregistered pardevice               
[  136.247995] ppdev0: registered pardevice                 
[  136.297222] ppdev0: unregistered pardevice               
[  137.444441] ppdev0: registered pardevice                 
[  137.492037] ppdev0: unregistered pardevice
```

Which doesn't seem to contain any error information regarding /dev/sda

Anyone have any ideas?

---

### Post by mcduck on 2009-03-30
You are trying to mount /dev/sda which is the drive. That won't work, you don't mount drives but partitions. /dev/sda1 for the first partition on that drive /dev/sda2 for second etc.

Please run "sudo fdisk -l" to list all your attached drives & partitions and post the output here. Actually posting your /etc/fstab could be useful as well.

---

### Post by DigitalNoise on 2009-03-30
> **mcduck said:**
> You are trying to mount /dev/sda which is the drive. That won't work, you don't mount drives but partitions. /dev/sda1 for the first partition on that drive /dev/sda2 for second etc.

Please run "sudo fdisk -l" to list all your attached drives & partitions and post the output here. Actually posting your /etc/fstab could be useful as well.
Funny you should mention that, but I finally figured that part out after I went for broke and installed ntfsprogs from the repository and used ntfsmount - which gave me more of an idea what I was doing wrong.

Once I passed it the right params it sure as heck mounted the drive just fine - I've actually got World of Warcraft running in Ubuntu right now; though the framerate is crap (but that's another thread for the Wine forums).

I guess the final question is - how do I make sure that the drive is mounted everytime I login?  I don't think I can specify to use ntfsmount in my fstab or my mtab files - or do I not need it, if I specify the following in the mtab:
```
/dev/sda1 on /media/xp type fuseblk (rw,nosuid,nodev,default_permissions,allow_other,blksize=4096,user=root)
```?

---

### Post by mcduck on 2009-03-30
TO get the drive mounted permanently you'd add it into fstab. (Yes, you can mount NTFS there, just like anything else that you can mount including network shares and other funny stuff).

But I can't really help you with the fstab syntax for NTFS partitions, last time I had NTFS was years ago and well before there was any NTFS write support available for Linux. You probably don't want to mount the drive as read-only so hopefully somebody else will be able to help with that.. :)

---

