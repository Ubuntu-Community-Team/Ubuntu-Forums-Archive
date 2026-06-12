---
title: "Several Hard Drive Questions."
date: 2009-05-24
forum: General Help
---

### Post by Roasted on 2009-05-24
So, my system was working all fine and dandy. I was in Vista gaming and decided, ya know, I'm done, I'm gonna go back to Linux.

WHA BAM! Then the hell began!

I have 4 drives in my system. They all mount in /etc/fstab by their UUID. 

Drive A - Vista/Ubuntu
Drive B - Copies my Ubuntu home directory
Drive C - Samba Network Drive
Drive D - Backup of Samba Network Drive

So I disconnected the 3 drives and worked on the system with ONLY my main drive. I was POSITIVE according to what everybody told me with the way I mounted them via UUID that I WOULD NOT require all 4 drives to be plugged in in order to boot my system. Except, my system fails to boot based on a failed file system check when I try to boot with 1 or more of the backup drives unplugged. The only way to successfully boot is to boot with all 4 drives - which is completely unacceptable because these are BACKUP drives. If they die, I need to still use the system.

Also - I noticed that the drive Device ID (/dev/sda etc) changed for 2 of my drives.

Drives A B C D are plugged into ports 1 2 3 4 onto my motherboard accordingly. I double and triple checked this. But somehow, drive B and C switched. Is this a big deal? Not really. Because the drives mount by UUID so each one is unique to itself.

But the issue at hand is this, I like seeing everything in an organized fashion in my system monitor. I like seeing:

Root Directory
Home Directory
LocalBackupDrive
StorageDrive
StorageBackupDrive

Not:

Root Directory
Home Directory
StorageDrive
LocalBackupDrive
StorageBackupDrive

It's just a pain and I don't understand why it changed. I thought /dev/sda naming conventions worked based on what port they are set up on with the SATA controller on the motherboard. So if it goes port 1, port 2, port 3, port 4, why does Ubuntu see it as Drive A, Drive C, Drive B, Drive D?

Does anybody know why I have to have all 4 drives functional to boot? The idea was to have my system be able to boot on the primary drive with the operating systems, and the other 3 drives were simply backups with no operating system or boot functionality. Why are these required now?

Thanks!

---

### Post by hal8000 on 2009-05-24
If all your linux partitions are on the same drive then you can boot without the other drives connected.

Can you boot with the live jaunty CD (if its Jaunty you are using) then post the output of:


sudo fdisk -l

blkid


This will give the information needed to find your partitions. Hard Drives in linux are created as block device files  /dev/sda /dev/hda etc, the first hard drive on the first IDE connector as master called a etc
The number after the drive letter represents partition number.

What else happened in Vista. A crash, unexpected error and did it shut down ok?

---

### Post by Roasted on 2009-05-24
Vista powered down fine. I had no issues with Vista when I was in it. It was when I rebooted that I got an error. After rebooting several times I obtained several other grub errors. I thought I had a hard drive die, but the BIOS revealed 4 drives plugged into the SATA ports. Okay fine, so I just kept trying different combinations to get it rolling again. Ultimately, I realized I had to have all of my drives plugged in to boot - which is NOT right.

Right now I'm booted up in the LiveCD as I type this. 

```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x16771676

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       10199    81923436    7  HPFS/NTFS
/dev/sda2           10200       60801   406460565    5  Extended
/dev/sda5           10200       10321      979933+  82  Linux swap / Solaris
/dev/sda6           10322       13360    24410736   83  Linux
/dev/sda7           13361       60801   381069801   83  Linux

Disk /dev/sdb: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xffffffff

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       30515   245111706   83  Linux

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0007269c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       60801   488384001   83  Linux

Disk /dev/sdd: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x43e0877d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1       30515   245111706   83  Linux
ubuntu@ubuntu:~$ sudo blkid
/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="78461C2D41973A21" LABEL="Vista" TYPE="ntfs" 
/dev/sda5: TYPE="swap" UUID="eacce669-8150-428b-9ac9-fe04025b027b" 
/dev/sda6: UUID="a11c8bb8-2175-4a8e-9813-0e67ac45e8a3" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda7: UUID="498359fb-1c75-474d-94ea-fcb26f84c012" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb1: UUID="772764b7-e571-4897-ba6d-ded412a5e814" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdc1: UUID="b2354e40-cd24-41eb-b41b-0aadc9933166" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdd1: UUID="b862f78f-4fcc-4d41-9d64-b7534da2dc84" SEC_TYPE="ext2" TYPE="ext3" 
ubuntu@ubuntu:~$ 

```

According to GParted, it sees 4 drives, but they're in a mixed order.

sda1 is 500gb = correct
sdb1 is 250gb = incorrect
sdc1 is 500gb = incorrect
sdd1 is 250gb = correct.

A and B should be 500gb.
C and D should be 250gb.

As I said, they're plugged into the ports on the board accordingly A 1, B 2, C 3, D 4, yet somehow Ubuntu is seeing B and C are mixed.

---

### Post by Roasted on 2009-06-04
I don't understand this. I rebooted from Vista and I noticed my bios screen was hanging longer than usual. Sure enough grub errored out. Now I'm just flat out frustrated because this issue happens entirely randomly for no reason. At first I thought it was just my computer trying to boot to USB, where I had my Sandisk mp3 player plugged in charging at the time.

So I went in the bios after grub errored out and checked out my drives. I had forgotten I completely reset my motherboard all together about 2 weeks ago when I was having issues.

I noticed it was on IDE mode. So I switched to AHCI mode which is what I was using before. Now my hard drives are all in line.

Why is this? I would REALLY like to know.

EDIT - 

I just duplicated what happened.

In /etc/fstab, I have the UUID's of the hard drives there. It seems in 9.04 whenever you boot up without a UUID present, you get an error on the screen. It's a command prompt looking screen and ultimately you see the UUID's listed of what's missing. In my case, it was my 3 backup drives, which were all unplugged. If you hit CONTROL + D as it says (after hitting enter) it seems that you can boot to the single drive then without the presence of the other drives missing from /etc/fstab. Well, I re-created the setup I had before. Like I said, when I reset my board it was defaulted to IDE mode, to where it seems my drives got mixed up with the Linux device tags. However, this is what I did.

-Booted to my single drive. Backup drives unplugged. Only my main OS drive plugged in.
-Changed BIOS to IDE mode.
-Powered off. Plugged in backup drives. Powered on.
-Ubuntu booted fine, but hard drive device tags were scattered.
-Powered off. Unplugged backup drives. Powered on with only my main OS drive.
-Booted to BIOS. Switched from IDE to AHCI mode.
-Powered off. Plugged in backup drives. Powered on.
-Booted to Ubuntu. Drives were in perfect alignment.

So take note, when I was changing from AHCI to IDE mode I was only using my main OS drive. The other drives were unplugged. 

It seems as if using AHCI mode seems to play nicer with Linux, since then the Linux device tags are based off of SATA ports in order. sda = port 1, sdb = port 2, etc.

Ultimately, is it bad to switch from IDE to AHCI mode (and vice versa) without doing a fresh install? Like I wonder if by me switching it in the first place was the reason I had any issues. I mean I had to because I reset the motherboard, but in order to get it working properly again, I had to disconnect all drives except my main one, boot up once, power off, THEN plug in my other drives. Then everything worked fine.

Can anybody explain to me why this is? Does it make sense to have to unplug all drives except the main one, then plug in the others to get AHCI mode to work fine after having it in IDE mode previously?

---

### Post by Roasted on 2009-06-07
bumpppp

---

### Post by tgalati4 on 2009-06-07
It looks like a an issue with how your motherboard BIOS enumerates disk drives when either in IDE (legacy) mode or AHCI mode.

Depending on how quickly the disk drives spin up and the when BIOS detects them can change.  This might impact UUID assignment--I'm not sure.

I've read of similar stories with Ubuntu on USB-external drives.  Sometimes Windows won't boot unless the USB drive is plugged in because when Windows was reinstalled, it expected the drive to be there even if it is not being used.  Strange behavior--but then again you are dealing with Windows.

You might have better luck keeping Vista on its own drive and put Ubuntu on a second drive with GRUB loaded to that drive's MBR.  Less chance of Windows messing up that way.

---

### Post by Krupski on 2009-06-07
> **Roasted said:**
> So, my system was working all fine and dandy. I was in Vista gaming and decided, ya know, I'm done, I'm gonna go back to Linux.

WHA BAM! Then the hell began!
................
Thanks!

For what it's worth... I use volume labels to avoid the "changing disk names" problem.

For example, my main install is "linux-root". The swap partition is "linux-swap". My mdadm RAID drive is "linux-raid".

So, to access, for example, my RAID drive, instead of using "/dev/md0", I use "/dev/disk/by-label/linux-raid" and it always works, regardless of how names get switched around.

UUID also works, but a readable name like "linux-root" is (in my opinion) nicer than "UUID=144d1a5f-1b1a-411a-a201-178403b0bca3".

Here's the FSTAB file from my file server box... all nice and neat and easy to read... no UUID!

```

root@storage:/# cat /etc/fstab 
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system>                 <mount point>   <type>  <options>       <dump>  <fsck>

# proc
proc                            /proc           proc    defaults        0       0

# root
/dev/disk/by-label/linux-root   /               ext3    relatime,errors=remount-ro 0       1

# swap
/dev/disk/by-label/linux-swap   none            swap    sw              0       0

# shared raid drive
/dev/disk/by-label/linux-raid   /home/shared    ext3    defaults        0       2

```

-- Roger

---

### Post by Roasted on 2009-06-08
I don't see a problem dealing with UUID, though. The main thing I care about is that my spare 500gb drive is indeed mounted to /media/localbackup, etc.

It was just convenient when my system assigned device tags (/dev/sda1, etc) to them based on the SATA port they were plugged into.

1 - A
2 - B
etc

That way when I go into system monitor to check out the file systems tab, I see all drives lined up in a sensible order.

I just didn't see why IDE mode switched them around while AHCI mode lined them up.

---

### Post by sedawk on 2009-06-08
Two things come to my mind:

1) With IDE drives you have this master-slave stuff. The
   numbering of disks might depend on which drives
   are used as master and which as slaves.

2) You can try to play with the fsck flag in /etc/fstab.
   If you turn off fsck during boot for partitions 
   from DISK B,C,D the system might boot automatically again
   if the disks are unplugged.
   On the other hand any entry in /etc/fstab might be regarded
   as a mandatory file system. So missing file systems are 
   indicating a serious problem. Optional disk should not
   be mounted via /etc/fstab.

---

### Post by Roasted on 2009-06-08
> **sedawk said:**
>  Optional disk should not
   be mounted via /etc/fstab.

I understand. I want all 4 of my drives to power on and get successfully mounted every single time my Ubuntu system starts. What I posted above was basically confusion, because in 8.10 I could reboot without even knowing that I had a dead drive, but now it seems 9.04 likes to notify you if a UUID did not mount when booting up. I was just so fired up when it happened I didn't realize it said CONTROL + D to resume normal boot. *shrug*

Nonetheless, this is starting to make sense and all is good. I'm just trying to understand what happened. I hate knowing a computer "got the best of me" so I always feel the need to know what is happening/happened, etc. Thanks for the responses! Any more input regarding this would be appreciated.

---

### Post by sedawk on 2009-06-09
You can think about using the "user, noauto" feature of /etc/fstab.

And if you need them you can mount them using your normal
user account.

---

### Post by Roasted on 2009-06-09
> **sedawk said:**
> You can think about using the "user, noauto" feature of /etc/fstab.

And if you need them you can mount them using your normal
user account.

To be honest, if I reboot and that screen comes up saying a drive failed to mount, it's like a warning sign to me that maybe a drive died. That's good, in my case. I just wanted to make sure that it was normal because in previous versions of Ubuntu, this wasn't the case. Seeing something different like that just made me think, oh crap, what happened... Know what I mean?

I like knowing if a drive is down. I just wanted to make sure this was acting "normal."

---

