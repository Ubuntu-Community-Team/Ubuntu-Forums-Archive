---
title: "grub Error 12: Invalid device requested"
date: 2009-05-08
forum: General Help
---

### Post by cglee on 2009-05-08
I have 8.10 64 bit ubuntu which had been working fine, I purchased a new hard drive to get more space, so i have 2 sata's the original drive had Windows XP first that died and my ubuntu
I added the new drive and put XP on it which worked fine but it killed my grub I was able to fix it that time by doing.

[LIST=1]
[*]Boot your computer up with Ubuntu CD
[*]Open a terminal window or switch to a tty.
[*]Go [SuperUser]("https://help.ubuntu.com/community/SuperUser") (that is, type "sudo -s"). Enter root passwords as necessary.
[*]Type "grub"
[*]Type "find /boot/grub/stage1". You'll get a response like "(hd0,1)". Use whatever your computer spits out for the following lines.
[*]Type "root (hd0,1)", or whatever your hard disk + boot partition numbers are for Ubuntu.
[*]Type "setup (hd0)", to install GRUB to MBR, or "setup (hd0,1)" or whatever your hard disk + partition nr is, to install GRUB to a partition.
[*]Quit grub by typing "quit".
[*]Reboot and remove the bootable CD.
[/LIST]

I couldn't leave well enough alone I wanted to get rid of the bad XP that resided on the old drive so I used partition manager and deleted that partition and merged it with some unpartioned space.
I then rebooted the system and grub was gone again i could not get into the system from Windows XP or ubuntu all i get is a black screen I have to hit control alt delete and this reboots the system I again tried the script up using a 8.04 live CD that I originaly loaded ubuntu with but now it wont let me load the Grub it gives me this message.

ubuntu@ubuntu:~$ sudo grub
Probing devices to guess BIOS drives. This may take a long time.

       [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]
grub> find /boot/grub/stage1
find /boot/grub/stage1
 (hd0,5)
grub> root (hd0,5)
root (hd0,5)
grub> setup (hd0)
setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  16 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd0) (hd0)1+16 p (hd0,5)/boot/grub/stage2 /boot/grub/menu.lst"... failed

Error 12: Invalid device requested
grub> 

What am I doing wrong please help I need my computer.
If I upgrade to 9.04 will this fix the problem

---

### Post by caljohnsmith on 2009-05-08
That kind of Grub error in the Grub command line is sometimes due to your HDD having a corrupt partition table. To see if that might be your problem, how about posting the output of the following commands:
```
sudo fdisk -lu
sudo sfdisk -d
sudo parted /dev/sda print
```
And we can work from there if you want.

John

---

### Post by cglee on 2009-05-08
Here is what I got from the items you suggested I retrieve
Thanks for your assistance.  
```

ubuntu@ubuntu:~$ sudo fdisk -lu
omitting empty partition (5)

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0ff50ff4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda2              63   184313744    92156841    7  HPFS/NTFS
/dev/sda3       184313745   245746304    30716280    7  HPFS/NTFS
/dev/sda4       245746305   312576704    33415200    5  Extended
/dev/sda5       245746368   309733199    31993416   83  Linux
/dev/sda6       309733263   312576704     1421721   82  Linux swap / Solaris

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x3abc3abb

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   204796619   102398278+   7  HPFS/NTFS
ubuntu@ubuntu:~$ 


ubuntu@ubuntu:~$ sudo sfdisk -d
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=        0, size=        0, Id= 0
/dev/sda2 : start=       63, size=184313682, Id= 7
/dev/sda3 : start=184313745, size= 61432560, Id= 7
/dev/sda4 : start=245746305, size= 66830400, Id= 5
/dev/sda5 : start=245746368, size= 63986832, Id=83
/dev/sda6 : start=309733263, size=  2843442, Id=82
# partition table of /dev/sdb
unit: sectors

/dev/sdb1 : start=       63, size=204796557, Id= 7
/dev/sdb2 : start=        0, size=        0, Id= 0
/dev/sdb3 : start=        0, size=        0, Id= 0
/dev/sdb4 : start=        0, size=        0, Id= 0
ubuntu@ubuntu:~$ 


ubuntu@ubuntu:~$ sudo parted /dev/sda print

Disk /dev/sda: 160GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system  Flags
 2      32.3kB  94.4GB  94.4GB  primary   ntfs              
 3      94.4GB  126GB   31.5GB  primary   ntfs              
 4      126GB   160GB   34.2GB  extended                    
 5      126GB   159GB   32.8GB  logical   ext3              
 6      159GB   160GB   1456MB  logical   linux-swap        

Information: Don't forget to update /etc/fstab, if necessary.             

ubuntu@ubuntu:~$
```

---

### Post by caljohnsmith on 2009-05-08
> **cglee said:**
> 
```

ubuntu@ubuntu:~$ sudo fdisk -lu
[COLOR="Red"]omitting empty partition (5)[/COLOR]

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0ff50ff4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda2              63   184313744    92156841    7  HPFS/NTFS
/dev/sda3       184313745   245746304    30716280    7  HPFS/NTFS
/dev/sda4       245746305   312576704    33415200    5  Extended
/dev/sda5       245746368   309733199    31993416   83  Linux
/dev/sda6       309733263   312576704     1421721   82  Linux swap / Solaris

```
As shown highlighted above, any time you get an "omitting empty partition (X)" error from fdisk, that's unfortunately a sure sign your partition table is corrupt; and because Grub is sensitive to problems with the partition table, that would explain your inconsistent Grub errors when doing the Grub commands. In your case, since you don't have any overlapping partitions, most likely the cause is that one of the EBRs (Extended Boot Records) points to another EBR that doesn't exist any more (the EBRs are associated with your logical partitions). But the good news is that problem is usually easy to fix, so how about doing the following command:
```
sudo fdisk /dev/sda
```
Press "w" and then enter, and that should fix the problem. What that does is simply rewrite your current partition table with all the original partition values, except fdisk is smart enough not to include the non-existent EBR. After you've done that, reboot, and try doing the following Grub commands:
```
sudo grub
grub> root (hd0,4)
grub> setup (hd0)
grub> quit
```
If you don't get any errors when running the above commands, reboot to your HDD, and let me know how far you get. We can work from there.

John

---

### Post by cglee on 2009-05-08
John you have the skills of a God!!! 
I am back up.
I did have to VI the menu.lst from hd0,5 due to the fact that  I changed it in the process of troubleshooting , it is now back to hd0,4 and ubuntu booted up just fine.

Thank you!!!!!

---

### Post by caljohnsmith on 2009-05-08
Glad to hear that worked OK and that you can boot into Ubuntu again. Cheers and have fun with Ubuntu. :)

John

---

### Post by IainPurdie on 2009-05-11
John, another quick "thank you" - that "fdisk" fix at the end was just what I needed to clear the same error message. I'd just migrated to a larger drive and shifted/resized some partitions.

Cheers!

---

### Post by intika on 2011-04-18
one more thank :D lol... resized my partition... and get this stuff... 
you got it dude ! 
(Chez nous on dit il est fort!!!!!!)

---

