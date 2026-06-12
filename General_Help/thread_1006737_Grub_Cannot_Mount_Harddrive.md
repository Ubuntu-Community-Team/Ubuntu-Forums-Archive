---
title: "Grub Cannot Mount Harddrive"
date: 2008-12-09
forum: General Help
---

### Post by Stoolcat on 2008-12-09
I needed to use some windows apps after being windows free for about 6 months, so I got out my installation CD and got it going.  I had already created a 20 gb Partition on my harddrive for it in Ubuntu, but when I tried to Install XP it said it couldn't be installed on the partition, to delete it and install on the blank space it created.  I installed with no problem, reinstalled and booted with the LiveCD to go ahead and restore GRUB.  I theb removed the LiveCD and rebooted.
Now whenever I try to boot using GRUB, Ubuntu won't boot. It says "cannot mount harddrive" So I put the liveCD back in and booted using that, I looked at the Partition Manager and it says that my harddrive is all unused.  I went to Places>Removable Media and all my partitions are there, and they are all mountable.  I would be happy to back up all my music and documents and just reformat the drive, but I don't have the means to do that.

My Fdisk -l
```
Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x38ef9d17

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         543     4361616    b  W95 FAT32
/dev/sda2   *         544         798     2048287+  83  Linux
/dev/sda3             799       24321   188948497+   5  Extended
/dev/sda5             799        3411    20988891    7  HPFS/NTFS
/dev/sda6           24182       24321     1124518+  82  Linux swap / Solaris
```


So.... how can I get GRUB to mount my harddrive?  If any other Information is needed, I will be more than happy to speedily reply.

Thanks in advanced.

---

### Post by Stoolcat on 2008-12-09
> **Stoolcat said:**
> 
```

/dev/sda3             799       24321   188948497+   5  Extended
/dev/sda5             799        3411    20988891    7  HPFS/NTFS

```


Okay, i Think I found the problem, my XP install (sda5) starts at the smae block as my Linux install (sda 3)  now I need to find a way to fix this... any ideas anyone?

EDIT: some of my files on my linux install are unreadable, so this further supports this theory, also they are some of the first files i transported onto my install...

---

### Post by caljohnsmith on 2008-12-09
It sounds like your HDD's partition table might be slightly corrupt. How about posting the output of the following commands:
```
sudo sfdisk -l
sudo parted /dev/sda print
```
Next make sure the Ubuntu Universe repository is enabled in System > Admin > Software Sources, and then download and run testdisk with the following commands:
```
sudo apt-get install testdisk
sudo testdisk
```
After starting testdisk with the above command, choose "no log", select HDD and "proceed", "Intel", "Analyze", and see what it shows for your HDD and what errors it might give. Please post the output of that screen. And lastly, see if you can mount any of your partitions as they currently are:
```
sudo mkdir /mnt/sda1 /mnt/sda2 /mnt/sda5
sudo mount /dev/sda1 /mnt/sda1
sudo mount /dev/sda2 /mnt/sda2
sudo mount /dev/sda5 /mnt/sda5
ls -l /mnt/sda1 /mnt/sda2 /mnt/sda5
```
And please post the output of all the above commands. We can work from there if you want. :)

---

### Post by Stoolcat on 2008-12-09
Thanks for replying and being willing to help.

sudo sfdisk -l
```
Disk /dev/sda: 24321 cylinders, 255 heads, 63 sectors/track
Units = cylinders of 8225280 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start     End   #cyls    #blocks   Id  System
/dev/sda1          0+    542     543-   4361616    b  W95 FAT32
/dev/sda2   *    543     797     255    2048287+  83  Linux
/dev/sda3        798   24320   23523  188948497+   5  Extended
/dev/sda4          0       -       0          0    0  Empty
/dev/sda5        798+   3410    2613-  20988891    7  HPFS/NTFS
/dev/sda6       3411   24180   20770  166835025   83  Linux
/dev/sda7      24181+  24320     140-   1124518+  82  Linux swap / Solaris

```


sudo parted /dev/sda print
```
Error: Unable to satisfy all constraints on the partition.  
```



testdisk output
```
Disk /dev/sda - 200 GB / 186 GiB - CHS 24321 255 63
Current partition structure:
     Partition                  Start        End    Size in sectors

 1 P FAT32                    0   1  1   542 254 63    8723232 [RECOVERY]
 2 * Linux                  543   0  1   797 254 63    4096575
 3 E extended               798   0  1 24320 254 63  377896995
A logical partition must contain only one partition
 5 L HPFS - NTFS            798   1  1  3410 254 63   41977782
 6 L Linux                 3411   0  1 24180 254 63  333670050
   X extended             24181   0  1 24320 254 63    2249100
 7 L Linux Swap           24181   1  1 24320 254 63    2249037

```


ls -l /mnt/sda1 /mnt/sda2 /mnt/sda5
```
total 118920
-rwxr-xr-x 1 root root         0 2008-12-09 15:59 autoexec.bat
-rwxr-xr-x 1 root root        53 2004-09-13 12:15 Autorun.inf
-rwxr-xr-x 1 root root       588 2005-08-05 17:22 batch.log
-rwxr-xr-x 1 root root       284 2002-05-30 10:24 batch.old
-rwxr-xr-x 1 root root       211 2008-12-09 15:53 boot.ini
-rwxr-xr-x 1 root root         0 2008-12-09 15:59 config.sys
-rwxr-xr-x 1 root root       102 2003-10-04 13:06 Desktop.ini
-rwxr-xr-x 1 root root      4096 2006-05-30 20:12 ffastun0.ffx
-rwxr-xr-x 1 root root      4109 2006-05-30 20:12 ffastun.ffa
-rwxr-xr-x 1 root root      8192 2006-05-30 20:12 ffastun.ffl
-rwxr-xr-x 1 root root      4096 2006-05-30 20:12 ffastun.ffo
-rwxr-xr-x 1 root root      8121 2003-06-12 17:52 Folder.htt
-rwxr-xr-x 1 root root         0 2005-08-05 17:22 full
-rwxr-xr-x 1 root root         0 2001-06-17 23:31 graph
-rwxr-xr-x 1 root root         0 2001-06-17 23:31 graph16
-rwxr-xr-x 1 root root         0 2005-10-09 11:27 hpcd.sys
drwxr-xr-x 5 root root      4096 2005-08-05 17:08 i386
-rwxr-xr-x 1 root root     40960 2002-09-10 15:54 Info.exe
-r-xr-xr-x 1 root root         0 2008-12-09 15:59 io.sys
-rwxr-xr-x 1 root root     23710 2005-08-05 17:22 MassStorage.log
-rwxr-xr-x 1 root root       918 2005-10-09 11:07 master.log
-rwxr-xr-x 1 root root         0 2004-05-04 10:46 menund
drwxr-xr-x 7 root root      4096 2005-08-05 17:17 MiniNT
-rwxr-xr-x 1 root root         0 2004-01-13 11:14 move
-r-xr-xr-x 1 root root         0 2008-12-09 15:59 msdos.sys
drwxr-xr-x 2 root root      4096 2008-03-29 17:29 New Folder
-r-xr-xr-x 1 root root     47564 2008-04-13 21:13 ntdetect.com
-rwxr-xr-x 1 root root         0 2004-01-13 11:14 ntfs
-r-xr-xr-x 1 root root    250048 2008-04-13 23:01 ntldr
-rwxr-xr-x 1 root root 120586240 2008-12-09 15:47 pagefile.sys
-rwxr-xr-x 1 root root        18 2006-01-07 21:27 prod
-rwxr-xr-x 1 root root    319545 2003-06-12 16:41 protect.ed
-r-xr-xr-x 1 root root         0 2005-10-09 11:07 RCBoot.sys
drwxr-xr-x 2 root root      4096 2005-08-05 18:17 Recycled
-rwxr-xr-x 1 root root    245920 2003-05-27 11:27 stldr
dr-xr-xr-x 2 root root      4096 2005-08-05 17:22 System Restore
drwxr-xr-x 5 root root      4096 2005-08-05 17:45 System Volume Information
drwxr-xr-x 8 root root      4096 2005-08-05 17:17 updgoi
-rwxr-xr-x 1 root root       486 2005-04-28 17:32 user
-rwxr-xr-x 1 root root     96774 2003-06-12 18:43 warning.bmp
-rwxr-xr-x 1 root root        10 2002-08-29 13:00 win51
-rwxr-xr-x 1 root root        11 2001-01-22 03:00 win51.b2
-rwxr-xr-x 1 root root        10 2001-08-23 11:00 win51ic
-rwxr-xr-x 1 root root        11 2001-03-20 03:00 win51ic.b2
-rwxr-xr-x 1 root root        11 2001-07-25 04:00 win51ic.rc1
-rwxr-xr-x 1 root root        11 2001-07-25 04:00 win51ic.rc2
-rwxr-xr-x 1 root root        10 2002-08-29 13:00 win51ip
-rwxr-xr-x 1 root root        11 2001-01-22 03:00 win51ip.b2
-rwxr-xr-x 1 root root        11 2001-07-25 09:47 win51ip.rc2
-rwxr-xr-x 1 root root         2 2002-08-29 13:00 win51ip.sp1
-rwxr-xr-x 1 root root        11 2001-07-25 04:00 win51.rc1
-rwxr-xr-x 1 root root        11 2001-07-25 09:47 win51.rc2
-rwxr-xr-x 1 root root       185 2001-09-13 20:29 winbom.ini
-rwxr-xr-x 1 root root         0 2004-01-13 11:14 xga

/mnt/sda2:
total 4
drwx------ 2 root root 4096 2008-12-05 13:45 lost+found

/mnt/sda5:
total 589864
drwxrwxrwx 1 root root      4096 2008-12-09 22:03 Documents and Settings
-rwxrwxrwx 1 root root 603979776 2008-12-09 22:02 pagefile.sys
drwxrwxrwx 1 root root      4096 2008-12-09 22:04 Program Files
drwxrwxrwx 1 root root      4096 2008-12-09 22:03 System Volume Information
drwxrwxrwx 1 root root     28672 2008-12-09 22:04 WINDOWS

```

thanks again

---

### Post by caljohnsmith on 2008-12-09
Unfortunately, you definitely have some problems with your HDD's partition table. Which partition has the personal files you want to back up? Because according to those last commands, you can access sda1, sda2, and sda5 just fine. Do you need to access the sda6 linux partition that sfdisk showed? If so, how about running testdisk again, but do the following: choose "no log", select HDD and "proceed", "Intel", "Analyze", "quick search", Y/N depending on if you have any Vista partitions, hit enter to continue, and select "Deeper Search" so it does a deeper search, which could take a while. Post the output of the screen that has the deep search results if you would like help recovering your partition.

---

### Post by Stoolcat on 2008-12-09
The files are on sda6, the one that is like 170Gb. 

Deeper Search
```
Disk /dev/sda - 200 GB / 186 GiB - CHS 24321 255 63
     Partition               Start        End    Size in sectors
* FAT32                    0   1  1   542 254 63    8723232 [RECOVERY]
P Linux                  543   0  1   797 254 63    4096575
D HPFS - NTFS            798   1  1  3410 254 63   41977782
D HPFS - NTFS            798   2  1  3232 254 63   39118149
P Linux                 3411   0  1 24180 254 63  333670050
L Linux Swap           24181   1  1 24320 254 63    2249037

```

thanks in advance

---

### Post by caljohnsmith on 2008-12-09
OK, since you just need to access the files on sda6, give this a try before we actually use testdisk to recover your partition table:
```
sudo mkdir /mnt/sda6
sudo losetup -o $((512*$(sudo sfdisk -luS 2>/dev/null | grep sda6 | awk '{print $2}'))) /dev/loop0 /dev/sda
sudo mount /dev/loop0 /mnt/sda6
gksudo nautilus /mnt/sda6 &
```
Please be sure to copy and paste that second command since it is important to get it exactly right, and please post the output of all the above commands. If those commands complete without error, that last command should enable you to browse all your files in sda6. Let me know if that works. :)

---

### Post by Stoolcat on 2008-12-09
sudo mount /dev/loop0 /mnt/sda6
```
mount: block device /dev/loop0 is write-protected, mounting read-only

```

gksudo nautilus /mnt/sda6 &
```
[1] 10401

```
sda6 then opened up in a file browser, and it seems browsable.  Under home there are no files or folders though.

EDIT: Wait, everything showed up, nevermind

---

### Post by Stoolcat on 2008-12-09
should i go ahead and reboot, or does my partition table need to be recovered?

---

### Post by caljohnsmith on 2008-12-09
So were you able to access all your personal files in sda6 OK and back them up? If so, you could just go with your plan of wiping the drive clean and reinstalling, or we could try to recover your partition table. Which do you prefer?

---

### Post by Stoolcat on 2008-12-09
I guess i would prefer to restore the partition table.  I can browse the files fine, no longer any problems with unreadable files.

---

### Post by caljohnsmith on 2008-12-09
> **Stoolcat said:**
> 
```
Disk /dev/sda - 200 GB / 186 GiB - CHS 24321 255 63
     Partition               Start        End    Size in sectors
[COLOR="Red"]P[/COLOR] FAT32                    0   1  1   542 254 63    8723232 [RECOVERY]
[COLOR="Red"]P[/COLOR] Linux                  543   0  1   797 254 63    4096575
[COLOR="Red"]*[/COLOR] HPFS - NTFS            798   1  1  3410 254 63   41977782
[COLOR="Red"]D[/COLOR] HPFS - NTFS            798   2  1  3232 254 63   39118149
[COLOR="Red"]L[/COLOR] Linux                 3411   0  1 24180 254 63  333670050
[COLOR="Red"]L[/COLOR] Linux Swap           24181   1  1 24320 254 63    2249037

```

OK, using the up/down arrow keys, select each partition in the results of the deep search, and then use the right/left arrow keys to mark each partition as shown above in the red highlighting. It might be that testdisk will only allow you to mark the first NTFS partition shown above as "L" and not "*", so use whichever it allows. Once you are sure you have all the partitions marked as shown above, press enter to get the next screen, and then choose "write" to write your new partition table. After that, post the new output of:
```
sudo fdisk -lu
sudo parted /dev/sda print
```
Or if it doesn't show the new partition table, go ahead and reboot and post the new results. We can work from there. :)

---

### Post by Stoolcat on 2008-12-09
i Can't get the Linux Partition (second one) to go to "L", it only goes to D,P,* and P and * make the structure "Bad", but I know I don' want to delete it...

---

### Post by caljohnsmith on 2008-12-09
OK, how about make the second linux partition "P", and then change the swap partition to "D"; that should hopefully work, and you can just use a swap file in Ubuntu instead of a swap partition. Or the other way I see would be to set either your Windows partition as "D" or the first FAT Recovery partition as "D", and then you can probably keep both the Linux partitions and the swap partition. It's up to you.

EDIT: Did you try setting the Windows partition as "L"? That might allow you to then set the second linux partition as "L".

---

### Post by Stoolcat on 2008-12-09
I set the second linux as P, and swap D.  Rebooted.  

sudo fdisk -lu
```
Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x38ef9d17

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63     8723294     4361616    b  W95 FAT32
/dev/sda2         8723295    12819869     2048287+  83  Linux
/dev/sda3   *    12819933    54797714    20988891    7  HPFS/NTFS
/dev/sda4        54797715   388467764   166835025   83  Linux

```


sudo parted /dev/sda print
```

Number  Start   End     Size    Type     File system  Flags
 1      32.3kB  4466MB  4466MB  primary  fat32             
 2      4466MB  6564MB  2097MB  primary  ext3              
 3      6564MB  28.1GB  21.5GB  primary  ntfs         boot 
 4      28.1GB  199GB   171GB   primary  ext3              

```

thanks again

---

### Post by caljohnsmith on 2008-12-09
OK, that's great news. Now to make sure that Grub is properly installed, how about doing:
```
sudo grub
grub> find /boot/grub/stage1
grub> find /grub/stage1
```
One of the above commands should return your main Ubuntu partition (or /boot partition if you have one) as either (hd0,1) or (hd0,3), but use whatever it returns as follows:
```

grub> root (hdX,Y)
grub> setup (hd0)
grub> quit
```
Please post the output of all the above commands. After that, reboot, and see how far you get on start up. Hopefully you'll be able to boot into Ubuntu, but if not, we can take care of the details. I just wanted to mention that I have to go now and won't be around for another 10 hours or so, but we can pick up then if you want.

---

### Post by Stoolcat on 2008-12-09
thanks for everything, I guess i will be on again in like 18 or so hours, but I might just abandon this and back up my data and do a fresh reinstall.  Thnaks again for all your help though

---

