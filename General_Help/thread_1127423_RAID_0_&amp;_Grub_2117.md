---
title: "RAID 0 &amp; Grub 21/17"
date: 2009-04-16
forum: General Help
---

### Post by k4$3 on 2009-04-16
I have a softRAID 0 setup with two identical SATA hdd's that holds my Windows, one 200gb PATA partitioned 100gb/100gb that holds Ubuntu, and one external 750 gb USB. Everything had been working with the Grub, until I had to plug in another SATA hdd off a friend's computer to scan and back up. It booted up fine, until I took my friend's drive out. Now my system will not boot up. I tried the original setup and got a Grub error 21 the first time, and a Grub error 17 every time following. I tried with my friend's drive with everything else in and got the same thing, same with just the RAID 0. I tried it with just the Ubuntu PATA and got an insert system disk error. Any help or ideas would be appreciated. I am relatively new to Linux, really new with Grub errors, and I'm really lost.

---

### Post by Alekz_ on 2009-04-16
Hi k4$3..

Post here your grub conf!

If you don't know how, its easy:

When you power-on your computer, the grub screen give you some options..
Hit "e" for _e_dit the content and you'll see the parameters which start your system!

:)

---

### Post by k4$3 on 2009-04-16
It won't even boot into the grub screen. It never gives me an option to go into anything other than the bios and softRAID screens, and I have tried just hitting E. Once again any help is appreciated, I rely on my computer for many things, including school.

---

### Post by ronparent on 2009-04-16
Boot the ubuntu live cd - 1st boot menu option. start a terminal - Application > Accessories > Terminal. Type:

sudo fdisk -lu

Post your output.

It appears your drive order has been resorted in bios. If we can figure the original order you may ba back in business.

---

### Post by k4$3 on 2009-04-16
Well I'm attempting to get a Live cd burnt but I'm having issues with the burner on this one. Until I get that fixed I tried reordering the hdd boot order in my Bios and I got an insert system disk error whenever the combination didn't start with my RAID array. When it did it would give me the same error 17

---

### Post by ronparent on 2009-04-16
If you know the id in bios of drive port you plugged into,you can try disabling it in bios. Other than that we are dead in the water without the live cd! 

Or if you have or can borrow a Vista dvd you can use it to fix the mbr on the raid array. That at least would get windows back up. You can then restore grub to the mbr when the live cd is available.

---

### Post by k4$3 on 2009-04-17
Ok I used another computer to burn the Live cd, I put it in my system, and the disk works like it should until it goes through the loading screen. Then when the loading screen finishes it turns off my monitor and I *hear* Linux boot up, but it doesn't show me anything. However, if I soft boot it will bring up the unloading screen, seemingly just to taunt me. Once again, I'm confused.

---

### Post by k4$3 on 2009-04-17
Never mind, got the Live disk to work.

 
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x47a447a3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   621072899   310536418+   7  HPFS/NTFS

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x05000000

Disk /dev/sdb doesn't contain a valid partition table

Disk /dev/sdc: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders, total 398297088 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x2c812c80

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1              63   386186534   193093236   83  Linux
/dev/sdc2       386186535   398283479     6048472+   5  Extended
/dev/sdc5       386186598   398283479     6048441   82  Linux swap / Solaris

Disk /dev/sdd: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x44fdfe06

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1              63  1465144064   732572001    c  W95 FAT32 (LBA)

---

### Post by k4$3 on 2009-04-17
/dev/sda & /sdb are my RAID 0 with XP
/dev/sdc *was* partitioned in half, with one partition Linux, the other NTFS, but I got overzealous and tried reinstalling Linux and using the whole drive
/dev/sdd is my external USB
if there is any more information needed I will gladly supply it. I just need to be able to boot into windows for now for homework

---

### Post by k4$3 on 2009-04-18
Ok I took what you said about the MBR and was able to boot into windows, however Linux will have to be fixed later. For anyone having the same issue here's what I did- 
put in your Windows disk, in my case XP Pro, boot to disk. 
When it loads I hit f6 to load RAID drivers, which I'm not sure was necessary. After that loaded I went into the recovery console, logged in, and ran 'fixmbr'. Rebooted and now everything is hunky dorey as far as Windows is concerned. I prefer using Linux, but I *need* Windows, and I just hope Linux will reinstall fine in the future. 
Thanks again for your help.

---

