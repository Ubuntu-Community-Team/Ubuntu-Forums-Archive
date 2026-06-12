---
title: "grub gone when u-10.04 installed after win7"
date: 2010-09-13
forum: Dell Ubuntu Support (CLOSED)
---

### Post by lookout4lpe on 2010-09-13
I am trying to reinstall Grub Bootloader after a wipe out by Win7.  I have a new dell 1745 with Win7 that I want to dual boot with Ubuntu 10.04.  I used the live CD method to install and have been successful creating the necessary partitions and getting Ubuntu installed and running.  One time.  I shut down and went to Win7 and then tried to startup with Ubuntu again and the bootloader was gone.  My problem is that as I follow the Windows Dual Boot Documentation, Master Boot Record and Boot Manager, live CD guide, everything works except step 5, running the grub-install command.  I have included a a listing showing my current partition setup and the step by step process I followed.  If you can point out the error of my ways you will make my day.  Thanks, Len

ubuntu@ubuntu:~$ sudo fdisk -l 
Disk /dev/sda: 500.1 GB, 500107862016 bytes 
255 heads, 63 sectors/track, 60801 cylinders 
Units = cylinders of 16065 * 512 = 8225280 bytes 
Sector size (logical/physical): 512 bytes / 512 bytes 
I/O size (minimum/optimal): 512 bytes / 512 bytes 
Disk identifier: 0xf6996dd3 

   Device Boot      Start         End      Blocks   Id  System 
/dev/sda1               1          13      102400   de  Dell Utility 
/dev/sda2   *          13        1926    15360000    7  HPFS/NTFS 
/dev/sda3            1926       30892   232676566    7  HPFS/NTFS 
/dev/sda4           30893       60802   240245761    5  Extended 
/dev/sda5           30893       59584   230467584   83  Linux 
/dev/sda6           59585       60802     9777152   82  Linux swap / Solaris 
ubuntu@ubuntu:~$ sudo mount /dev/sda5 /mnt 
ubuntu@ubuntu:~$ ls 
Desktop  Documents  Downloads  Music  Pictures  Public  Templates  Videos 
ubuntu@ubuntu:~$ sudo grub-install --root-directory=/mnt/ dev/sda5 
/usr/sbin/grub-probe: error: cannot stat `dev/sda5'. 
Invalid device `dev/sda5'. 
Try `/usr/sbin/grub-setup --help' for more information. 
ubuntu@ubuntu:~$

---

### Post by drs305 on 2010-09-13
> **lookout4lpe said:**
> If you can point out the error of my ways you will make my day.  Thanks, Len

ubuntu@ubuntu:~$ sudo mount /dev/sda5 /mnt 


The **[COLOR="Red"]/[/COLOR]** ended up in the wrong place and you install only to the drive, not the partition:
From:
> sudo grub-install --root-directory=/mnt**[COLOR="Red"]/[/COLOR]** dev/sda5
To:
> sudo grub-install --root-directory=/mnt **[COLOR="DarkRed"]/[/COLOR]**dev/sda

---

### Post by lookout4lpe on 2010-09-13
First, thank you for your reply.  I hope I did not commit another !#$% error.  But I do get a warning – not to proceed.  You will notice that I used two formats for the slash ‘/’.  The format printed in the guide, ..mnt/ /dev.. and your correction, ..mnt /dev..  Both resulted in the same error.  I do not know how to apply "--force--"  I hope you may see the correction needed.

ubuntu@ubuntu:~$ sudo fdisk -l
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xf6996dd3
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          13      102400   de  Dell Utility
/dev/sda2   *          13        1926    15360000    7  HPFS/NTFS
/dev/sda3            1926       30892   232676566    7  HPFS/NTFS
/dev/sda4           30893       60802   240245761    5  Extended
/dev/sda5           30893       59584   230467584   83  Linux
/dev/sda6           59585       60802     9777152   82  Linux swap / Solaris
ubuntu@ubuntu:~$ sudo mount /dev/sda5 /mnt
mount: /dev/sda5 already mounted or /mnt busy
mount: according to mtab, /dev/sda5 is already mounted on /mnt
ubuntu@ubuntu:~$ sudo grub-install --root-directory=/mnt/ /dev/sda5
/usr/sbin/grub-setup: warn: Attempting to install GRUB to a partition instead of the MBR.  This is a BAD idea..
/usr/sbin/grub-setup: warn: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and its use is discouraged..
/usr/sbin/grub-setup: error: if you really want blocklists, use --force.
ubuntu@ubuntu:~$ sudo
sudo      sudoedit  
ubuntu@ubuntu:~$ sudo grub-install --root-directory=/mnt /dev/sda5
/usr/sbin/grub-setup: warn: Attempting to install GRUB to a partition instead of the MBR.  This is a BAD idea..
/usr/sbin/grub-setup: warn: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and its use is discouraged..
/usr/sbin/grub-setup: error: if you really want blocklists, use --force.
ubuntu@ubuntu:~$

---

### Post by drs305 on 2010-09-13
I edited my response further, added color for highlighting and made sure the install command was correct. The mount can be written as /mnt or /mnt/, it doesn't seem to matter but you need a / immediately before *dev*  (/dev/sda5).

You are trying to install Grub on a partition, which G2 does not like. You mount the partition (sda5) but you run the install command on the *drive*. This will install Grub2 in the MBR of sda and write the files to the sda5 partition.
```

sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt /dev/sda

```

---

### Post by lookout4lpe on 2010-09-13
No Joy!  Process ran without any problems.  Showed no errors.  But, shutdown and started win7, OK.  Shut down and tried Ubuntu, no way.  See you tomorrow.  Thanks

---

### Post by drs305 on 2010-09-13
:-(

When you have time, post the contents of *meierfra's* boot info script (between code tags generated by pressing the # icon in the post's menu):
[http://bootinfoscript.sourceforge.net/]("http://bootinfoscript.sourceforge.net/")

There is also this:
[How to restore the Ubuntu/XP/Vista/7 bootloader]("http://ubuntuforums.org/showthread.php?t=1014708")

---

### Post by lookout4lpe on 2010-09-14
The results file is attached for your review.  I will now look at the second item and wait for your findings on the boot info script.  Thank you.

---

### Post by lookout4lpe on 2010-09-15
I looked at the "How to Restore Bootloader" article.  

The first how-to is the same restore process that we used to get the Ubuntu bootloader to work.  But it worked only one time.  Starting up and selecting to boot to win7 worked, but shutdown and then booting to ubuntu or win7 was not possible (no dual bootloader).   

The second how-to does not apply to unbuntu 10.04.  

The third how-to was and was not successful.  I do not have a win7 install disk, only a system repair disk I make last week when I took the laptop out of the box.  The system repair disk booted and ran for 2-3 minutes, then displayed an error code, and locked up.  I went online and downloaded a recovery disk for win7 and it booted, went past the keyboard setting, then found the operating system.  It then asked if I wanted the startup repaired.  After saying yes the repair was completed and I started up and selected win7.  Win7 loaded and I completed a few tasks and then shut it down.  Again at startup no boot loader was found to start ubuntu or win7.

My take from this is that Dell, Win7, and Ubuntu 10.04 will not co-exist.  It appears that the the dual boot loader is placed in a location that is altered or written over at win7 shutdown so that it is not available for the next try at a dual boot.  I would guess that the Dell backup and recovery partitions are part of the problem.  

Have you discovered any issues in your review of the boot info script?

Is there a solution to this problem?

Thanks for your help,  Len

---

### Post by lookout4lpe on 2010-09-15
I have searched and found that this issue can be solved by uninstalling the dell data safe applicaitons.

[http://www.linuxforums.org/forum/ubuntu-linux-help/162584-solved-win-7-ubuntu-dual-boot-grub-problem.html](http://www.linuxforums.org/forum/ubuntu-linux-help/162584-solved-win-7-ubuntu-dual-boot-grub-problem.html)

[http://superuser.com/questions/129926/grub-loading-the-symbol-not-found-aborted-press-any-key](http://superuser.com/questions/129926/grub-loading-the-symbol-not-found-aborted-press-any-key)

An alternate solution is suggested here that uses GRUB2 and does not require that dell data safe apps be eliminated.  Is is viable?

[http://ubuntuforums.org/showthread.php?p=9166484#post9166484](http://ubuntuforums.org/showthread.php?p=9166484#post9166484)

Given that some agreement is forming around the why, which solution do you recommend?

---

### Post by drs305 on 2010-09-15
> **lookout4lpe said:**
> 
Have you discovered any issues in your review of the boot info script?

Is there a solution to this problem?

Len,

I looked at the script and as far as the Linux stuff goes it looks correct. I'm not a Windows guy, especially Vista and later, and so I can't say what's happening with them. 

Hopefully a Windows person will view the post and offer some advice.

---

### Post by lookout4lpe on 2010-09-16
I want to close this thread with a few conclusions.

First, drs305 has been very helpful in navigating toward a solution of my problem.  He/she was also my motivation to continue looking for a solution.  I have come to a conclusion as far as my issue is concerned.  I have decided to uninstall the data safe applications on my dell laptop.  Two reasons, one, it solved my problem and, two, the reviews I read said there are better apps out there, just look.  Thanks drs305.

Second conclusion.  Somebody else has already solved the problem.  Its just hard to find somebody.  Microsoft several years ago reported that you could use a repair program that was on the install disk to repair startup issues in windows. I have attached and article and the MS Article ID: 927392.  Since I donot have a install disk and have not taken the time to find the bootrec.exe tool on my dell recovery partition on my laptop, I have not tested this solution.  I am happy with my first conclusion.

---

