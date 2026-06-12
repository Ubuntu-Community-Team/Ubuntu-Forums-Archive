---
title: "problems with GRUB&gt;"
date: 2011-04-18
forum: Desktop Environments
---

### Post by ujjal on 2011-04-18
I am new to ubuntu 10.10 .I used xp and ubuntu parallely. Suddenly I found that,when I try to enter ubuntu, there is a black window where a grub command is being required like [COLOR=Red]grub>
[COLOR=Navy]I can't enter on Ubuntu  [/COLOR][/COLOR]
I have read some posts about this problem but didnt get any solution.I dont want to reinstall ubuntu. So, please help me.


Thanks in advance

---

### Post by Rubi1200 on 2011-04-18
Hi,

please do the following so we can see what is going on:

Boot the Ubuntu Live CD/USB. Choose the option "Try Ubuntu without any changes." Once the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded, move the boot info script to the desktop.
3. Open a terminal and run the command

```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by 3Miro on 2011-04-18
Grub problems could be due to many things. Right before the grub> line, there should be an error message. What does it say?

---

### Post by 3Miro on 2011-04-18
> **Rubi1200 said:**
> Hi,

please do the following so we can see what is going on:

Boot the Ubuntu Live CD/USB. Choose the option "Try Ubuntu without any changes." Once the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded, move the boot info script to the desktop.
3. Open a terminal and run the command

```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

cross post. This is a better way to diagnose the problem.

---

### Post by ujjal on 2011-04-18
Sorry for the late. It took too much time to boot. Here is the result.txt

```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM /wubildr.mbr /wubildr

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   /ubuntu/winboot/wubildr.mbr /ubuntu/winboot/wubildr 
                       /ubuntu/disks/swap.disk

sda6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda6 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda7 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda8: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sda8 starts 
                       at sector 0. But according to the info from fdisk, 
                       sda8 starts at sector 343276983.
    Operating System:  
    Boot files/dirs:   

sda9: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda9 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda10: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda10 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    61,432,559    61,432,497   7 HPFS/NTFS
/dev/sda2          61,432,560   625,121,279   563,688,720   f W95 Ext d (LBA)
/dev/sda5          61,432,623   155,380,679    93,948,057   7 HPFS/NTFS
/dev/sda6         155,380,743   249,328,799    93,948,057   7 HPFS/NTFS
/dev/sda7         249,328,863   343,276,919    93,948,057   7 HPFS/NTFS
/dev/sda8         343,276,983   437,225,039    93,948,057   7 HPFS/NTFS
/dev/sda9         437,225,103   531,173,159    93,948,057   7 HPFS/NTFS
/dev/sda10        531,173,223   625,121,279    93,948,057   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        00CCA083CCA07496                       ntfs       Xp                            
/dev/sda10       1448BAF248BAD22A                       ntfs       Movies                        
/dev/sda2: PTTYPE="dos" 
/dev/sda5        EA90442A90440015                       ntfs       Ubuntu                        
/dev/sda6        3830B02A30AFECD6                       ntfs       Softwares                     
/dev/sda7        88DC0E80DC0E68B0                       ntfs       Books & Photos                
/dev/sda8        201E-E82A                              vfat       CARTOON                       
/dev/sda9        861CAACB1CAAB599                       ntfs       Song                          
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda10       /media/Movies            fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda9        /media/Song              fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 
C:\wubildr.mbr = "Ubuntu"

```

---

### Post by Rubi1200 on 2011-04-19
According to the results you installed Ubuntu using the Windows installer Wubi.

The problem is that you are missing the root.disk where all the essential files are stored.

This is what you can try; boot into Windows and enable the option to see hidden files and folders and then look for files named > found.000

If the root.disk is there, just copy it back to the main Ubuntu folder and you should be good again.

If you do not find it, please let us know.

---

### Post by ujjal on 2011-04-19
there is no file named "found.000" .Now what to do?

Thanks in advanced.

---

### Post by Rubi1200 on 2011-04-19
I would try using the advanced search function in Windows. But, unless you made a backup you might have to reinstall.

Without the root.disk Wubi/Ubuntu will not work.

Do you have any idea what might have happened to cause this?

---

### Post by ujjal on 2011-04-19
Then what are you suggesting to me? Should I re install ubuntu?

---

### Post by Rubi1200 on 2011-04-19
Hi ujjal,

If you are unable to find the root.disk then, yes, you have no choice but to reinstall.

However, before you do that have another look. Perhaps there is a file named found.001 etc.

What I am saying is that Windows has a built-in search function and you should enable its advanced features to try and find the root.disk.

Other than that, there is no way to fix this unless you happen to have made a backup copy of the root.disk.

Sorry I don't have better news for you.

---

### Post by ujjal on 2011-04-19
Got it .Thanks for your help. Please give answer of my questions about ubuntu.

1. After installing ubuntu should I make an backup on HDD?
    ans: yes

2. XP / ubuntu
    C  / sda1
    D  / sda2
    E  / sda5
    F  / sda6
so on....? Am I right?

3.The problem I am facing [for which this thread is],when it will occure ? What are the   precautions ?

4.Which is better between boot install and through wubi.exe ? 
 
These questions may be simple but I am new to ubuntu and liked it.

---

### Post by Rubi1200 on 2011-04-20
Hi,

let me try and answer some of your questions, but understand there are different approaches and my suggestions may not be the best for your situation. In the end, you need to decide what you want.

Backups; you should ALWAYS be backing up your data, whether it is in Windows or Linux

Wubi or a proper dual-boot install? Again, this is a personal decision. Wubi is great if you don't want to mess around with partitioning, bootloaders, and other such stuff. On the other hand, if you know you like Ubuntu and think you will use it at least 50% of the time, then a real install to the hard-drive is better.

> The problem I am facing [for which this thread is],when it will occure ? What are the   precautions ?
Not sure I understand what you mean here; are you talking about the problems with a Wubi install?

> C  / sda1
    D  / sda2
    E  / sda5
    F  / sda6
Is this the current layout of your drive or how you want it to look after partitioning?

You can only have 4 primary partitions, so in most cases you would either delete a partition and create an extended partition with a logical partition for Ubuntu or use Wubi, which doesn't have issues with 4 primary partitions unless the disks are dynamic.

---

