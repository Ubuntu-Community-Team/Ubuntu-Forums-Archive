---
title: "Multi OS - Multi Drive Problem"
date: 2009-11-27
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Ishelk on 2009-11-27
Hi,

I have a DELL studio 1737 laptop with two hard drives. I was using Vista all this time. I downloaded Ubuntu and installed it today. Since I have two hard drives, my intenstion was to install them in two different drives and use BIOS boot order to switch between them. So I physically removed the hard drive with Vista and installed Ubuntu in the other. 

Ubuntu worked fine. But when I reconnected the drive with Vista, I cannot boot using that. I assumed two drives have their own BMRs and would work independently. 

Where did I go wrong and how can I recoved my vista boot ability?

Thanks in advance
Ishan

---

### Post by efflandt on 2009-11-27
It would help to determine the reason for your issue if you said what specific error message you get, if any, when Vista fails to boot.  For example, "no operating system" may indicate an attempt to boot a drive with no mbr.  A missing or corrupt sys or dll might indicate that Windows ntldr doe not find Windows on the partition it thinks it should be on, due to drive order change.  Similarly, a grub error might be that grub cannot find the rest of itself, due to drive order change.

The mbr is where it was put, either intentionally or accidentally.  Typically if you only had one physical drive when an OS was installed, the mbr would be on that drive.  But if you originally had more than one drive when Vista was installed, it may depend upon what was considered the primary drive at the time by BIOS or any boot loader or manager.  Or in the case of grub, it depends where you decided to put it, or whether you accepted the default.

If your computer came with more than one physical drive, it may depend upon if the drives are on the same cable, how the drives were jumpered (master/slave), or if cable select instead, which plug on the cable is plugged into each drive, and/or which drive you told BIOS to boot.

When you installed Ubuntu with only 1 drive at the time, by default it put grub (or grub2) in the mbr of that drive, unless you selected to install it to a partition instead in the **Advanced** button near the end of Ubuntu install.  And that grub/grub2 expects to find the rest of its loader on the partition it was on when it was installed.  And if you then insert a drive that changes the drive order, grub may error when you try to specifically boot from that drive.

If you boot from Ubuntu (or gparted-live) CD and look at the partitions (or output of sudo fdisk -l), it might tell you which drives are currently seen as primary or secondary.

---

### Post by balloooza on 2009-11-27
[http://ubuntuforums.org/showthread.php?p=8396719#post8396719](http://ubuntuforums.org/showthread.php?p=8396719#post8396719)

I am here looking at some simelar problems.

One thing that you may not have known is that ubuntu has a bootloader built in, and when you install it (it being the bootloader, but ubuntu installs it and configures it automaticly) it detects all the operating systems. BUT, you need to ave booth disks pluged in when you install, This other person on the other thread did the same thing, it is just unneccecary, ubuntu will not overwrite windows, try this, just reinstall ubuntu with booth hard drives connected, and when in the partition selector, make sure that you are using the non windows disk, and install, then, presto, next time you boot up, you will have the choice, since you are a beginner, I think that this is the best way and also becuase you have not put much into ubuntu yet

---

### Post by Ishelk on 2009-11-27
Thanks guys, 

Well I tried to digg in bit deep and actually I might have overwritten my Vista boot record. Following is the output of fdisk -l. 

[COLOR=DarkOrchid][I]Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x10000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          18      144553+  de  Dell Utility   [COLOR=Black]{Dell Partition}[/COLOR]
/dev/sda2              19        1324    10485760    7  HPFS/NTFS [COLOR=Black]{Recovery Partition}[/COLOR]
/dev/sda3   *        1324       19780   148249596    7  HPFS/NTFS [COLOR=Black]{Vista installation}[/COLOR]
/dev/sda4           19780       30402    85316608    f  W95 Ext'd (LBA)
/dev/sda5           19780       30402    85315584    7  HPFS/NTFS

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2f899920

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       13055   104857600    7  HPFS/NTFS
/dev/sdb2           13055       21761    69933182    7  HPFS/NTFS
/dev/sdb3           21762       30401    69400800    5  Extended
/dev/sdb5   *       21762       30043    66525133+  83  Linux
/dev/sdb6           30044       30401     2875603+  82  Linux swap / Solaris[/I][/COLOR]

I have vista in /dev/sda3. So I tried to add *set root = (hd0,2)* into grub.cfg. It resulted with an error like "Drive with No MBR" or similar message. That was where I expected to have my vista MBR. 

[COLOR=DarkRed]balloooza:[/COLOR] First I tried to install with the both hard drives connected. but during the installation it showed me only the second hard drive. ( where I installed ubuntu at the end)

Thru Ubuntu I can browse the Vista drives. So is there a way to reconstruct the BMR for vista and write it to sda3 .... or add an entry to grub so it can boot Vista. {Its strange that grub has pickup an old Windows 7 entry at (hr0,3) } 

I have the option of wiping out every thing and install... But I am determined to learn Ubuntu ,,,,, :D

Thanks in advance,
Ishan

---

### Post by Ishelk on 2009-11-28
I ran the testDisk Utility and the log says the Vista partition has a boot sector and it is ok ..
[COLOR=Purple][I]ntfs_boot_sector
 3 * HPFS - NTFS           1323 132 26 19779 188 49  296499192
     NTFS, 151 GB / 141 GiB
NTFS at 1323/132/26
Info: size boot_sector 296499032, partition 296499192
NTFS at 1323/132/26
filesystem size           296499032 296499192
sectors_per_cluster       8 8
mft_lcn                   786432 786432
mftmirr_lcn               29195775 29195775
clusters_per_mft_record   -10 -10
clusters_per_index_record 1 1
Boot sector
Status: OK

Backup boot sector
Status: OK

Sectors are not identical.

A valid NTFS Boot sector must be present in order to access
any data; even if the partition is not bootable.

TestDisk exited normally.[/I][/COLOR]

I still don't understand the problem... When I boot from the Vista drive now I get error "A disk read error occured. Pres Ctrl+Alt+Del to restart". But I can read file structure from Ubuntu :( I am confused. Fedup of this now.... Appreciate if someone can help.... will see till tomorrow ,,,,, Strangely, I figure out that the vista installation Cd is also not running well ,,,, Sort of stuck with no error message :(

---

