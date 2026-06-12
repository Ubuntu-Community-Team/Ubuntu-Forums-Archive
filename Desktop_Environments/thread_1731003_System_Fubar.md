---
title: "System Fubar"
date: 2011-04-16
forum: Desktop Environments
---

### Post by scritchmus on 2011-04-16
Okay. Here's the scoop!

Really hoping someone can help.

I downloaded Ubuntu 10.10 32-bit for Desktop.
Burned the .iso to CD and ran it from CD without installing.

It worked great as long as I checked the nomodeset option under F6. (I'm assuming this has something to do with ATI Radeon video drivers?)

So it worked and I wanted to install onto a HDD for faster operations.

My system has 3 HDD's.

HDD 1 and 2 are 160GB Seagates set up as a RAID0 array - as stripe0 and stripe1. This is my WindowsXP bootable drive.

HDD3 is a 40GB Maxtor drive formatted NTFS but not bootable. Just an old extra drive I use for storage and backup.

So I installed Ubuntu using the "Alongside Windows" option and directed the installer to create a partition on the 40GB Maxtor and install itself there.

The installer then split the drive roughly in half, keeping my NTFS stuff on one partition and making the other partition ext4 and installing Ubuntu there.

So far so good.

Then I did a reboot and entered the 9th circle of hell.

Computer never booted into Ubuntu nor can it boot into XP anymore.

Here's what I attempted so far:

Went into Windows Recovery Console:
    FIXMBR
    FIXBOOT

Still nothing.

BOOTCFG /SCAN reveals that it can't find any Windows installations. Great!

Even tried:

   sudo apt-get install lilo
   sudo lilo -M /dev/sda mbr

from Ubuntu to see if that might work.
Nope.

From what I can gather so far, it looks like I lost the partition table on my RAID drive.

Windows cant find it anymore, but I can see the drive in Ubuntu, I can open it, I can open Folders, I can open/copy/move files. (This is at least a good thing since I can backup files if I need to rebuild the RAID array.)

gparted see's my RAID array as sdb and sdc. On both it says "Partition unallocated"

sdb has a warning: "Can't have partition outside the disk"
sdc has a warning: "Unrecognized disk label"

So. Is there any way to repair my RAID partition table  (using Ubuntu) so that Windows can see it again and boot into XP?

Why did Ubuntu destroy my partition table on the RAID array drives when I told it to install onto a partition on the other 40GB HDD?

Since I can access the RAID drive through Ubuntu and save my important stuff, I can rebuild the RAID array if need be and start over. But I would rather avoid that if I can.

Why is it that Windows cant see the RAID array anymore, yet Ubuntu can? I take it this is due to Ubuntu's superiority as an OS! Even though the partition tables are destroyed on the RAID array drives, Ubuntu is still able to take the two striped drives and assemble the data such that I can see all files and folders. Take that Microsoft!!

Please Help!!!!

Thank you!!

---

### Post by Copper Bezel on 2011-04-16
I don't know RAID, but one thing I can tell you is that whatever partition you select from the installer to install Ubuntu onto, unless you indicate otherwise, will become the bootable partition with the MBR and GRUB. I've done this with a *flash drive*, to much hilarity.

Again, though, I don't know RAID, and your Windows partition table certainly shouldn't have been affected by a change of one boot flag.

---

### Post by oldfred on 2011-04-16
I do not know RAID either. But post this so someone can see the details:

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.

I thought the desktop installed did not include the RAID driver/tools and you had to use the alternative installer. But Ubuntu installed from a desktop sees your RAID? perhaps it saw the RAID and downloaded those as part of the install.

---

### Post by scritchmus on 2011-04-17
I have since re-formatted the 40GB HDD that I installed Ubuntu to. Mainly to have space to copy important files to from the RAID array drives. 

Keep in mind that I'm not too concerned with the Ubuntu install for now. I just want to get my RAID array back so that I can boot into XP. Then I will inquire about the CORRECT way to set up a dual-OS system with XP on the RAID0 array and Ubuntu on the other 40GB HDD.

Here is the results of the boot info script:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => No boot loader is installed in the MBR of /dev/sda
 => Lilo is installed in the MBR of /dev/sdb
 => Windows is installed in the MBR of /dev/sdd
 => Lilo is installed in the MBR of /dev/mapper/via_ddbaabaefd

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sdd1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

via_ddbaabaefd1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders, total 80293248 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048    80,292,869    80,290,822   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   625,137,344   625,137,282   7 HPFS/NTFS

/dev/sdb1 ends after the last sector of /dev/sdb

Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 8019 MB, 8019509248 bytes
20 heads, 16 sectors/track, 48947 cylinders, total 15663104 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdd1    *             80    15,663,103    15,663,024   b W95 FAT32


Drive: via_ddbaabaefd ___________________ _____________________________________________________

Disk /dev/mapper/via_ddbaabaefd: 320.1 GB, 320083722240 bytes
255 heads, 63 sectors/track, 38914 cylinders, total 625163520 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/mapper/via_ddbaabaefd1   *             63   625,137,344   625,137,282   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/mapper/via_ddbaabaefd1 E66C36F36C36BE5D                       ntfs                                     
/dev/mapper/via_ddbaabaefd: PTTYPE="dos" 
/dev/sda1        1174F7BC1AECD0B0                       ntfs       New Volume                    
/dev/sda: PTTYPE="dos" 
/dev/sdb                                                via_raid_member                               
/dev/sdc                                                via_raid_member                               
/dev/sdd1        6C1B-5271                              vfat       CORSAIR                       
/dev/sdd: PTTYPE="dos" 
error: /dev/sdb1: No such file or directory

=============================== "ls -R /dev/mapper/" output: ===============================
/dev/mapper:
control
via_ddbaabaefd
via_ddbaabaefd1

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr1         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdd1        /media/CORSAIR           vfat       (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,showexec,flush)
/dev/mapper/via_ddbaabaefd1 /media/E66C36F36C36BE5D  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda1        /media/New Volume        fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)

=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb1



=============================== StdErr Messages: ===============================

hexdump: /dev/sdb1: No such file or directory
hexdump: /dev/sdb1: No such file or directory
```

Hope this helps

---

### Post by Copper Bezel on 2011-04-17
Helps me to exit the thread rather gracelessly, as I'm already wrong; your MBR is where you left it. Damn.

---

### Post by oldfred on 2011-04-17
The script is giving two clues, but with RAID I have not idea how to fix. If standard partitions I might use testdisk.

Usually some sort of file corruption, may need chkdsk or just be partition table issue.
mount: unknown filesystem type ''
Is partition table issue in standard partitions.
/dev/sdb1 ends after the last sector of /dev/sdb

It is also not showing your 
/dev/mapper/via_ddbaabaefd2
it just has:
/dev/mapper/via_ddbaabaefd1

Do you install the mdadm package?

Install these before running script:
Is able to search LVM partitions if the LVM2 package is install
# ("apt-get install lvm2" in debian based distros)
# Is able to search Linux Software Raid partitions (MD Raids) if
# the "mdadm" package is installed.
[http://grub.enbug.org/LVMandRAID](http://grub.enbug.org/LVMandRAID)

If you had included RAID in your title of this thread, it would help has a few here do know RAID, but most only look for titles relating to what they may know.

---

### Post by scritchmus on 2011-04-23
Well I am not getting any help with this thread. I want to start a new one with the word RAID in the title to get RAID related responses. Should I mark this thread as solved?

---

### Post by Copper Bezel on 2011-04-23
I guess you could try flagging down a mod to change the title. I think the better bet, along with the more descriptive title, would be starting your new thread or getting this one moved over to Hardware & Laptops as opposed to Desktop Environments.

---

### Post by scritchmus on 2011-04-23
Why "Hardware and Laptops"?

---

### Post by oldfred on 2011-04-23
I would suggest server, as they use RAID more. Desktops do not. But title is more important than anything. Then description. Repost latest boot info script.

Threads in Forum : Server Platforms
[http://ubuntuforums.org/forumdisplay.php?f=339](http://ubuntuforums.org/forumdisplay.php?f=339)

---

### Post by scritchmus on 2011-04-24
Ok. Will do. Thanks for everything so far!

---

