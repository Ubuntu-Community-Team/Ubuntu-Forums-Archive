---
title: "ubuntu 9.04 failed, 10.10 not installing"
date: 2010-11-26
forum: Dell Ubuntu Support (CLOSED)
---

### Post by warda on 2010-11-26
hi there,
 
I have dell latitude 131l running Vista with no problems at all. 
Wanted to try Ubuntu desktop and so installed 9.04 LTS as dual boot. It lasted for 1 day and half only!
after that whenver I was tryingto boot in ubuntu it was taking me to comand line and saiyng **initramfst** or something like that  - cant remember sorry.
anyhow I though ok ubuntu is broken I install the newest version. so downloaded 10.10 but whenver I try install it goes to the place where you choose partition. I click continue and it says that will might take a while but that's it. it freeze on this stage. I tried couple of times. last night I left it overnight it still was in the same place.this can't be right?
I use unetbootin-windows-494 to boot it from usb. 
I dlove to try ubuntu dsktop but can't see it working so far?
any ideas how I can get it on my laptop? (thought it really was going to straight forwards...)
 
if no hope cna someone tell me how to remove linux dual boot screen so it will go straight to vista?
 
thank you

---

### Post by wilee-nilee on 2010-11-26
Using the live Ubuntu cd run the bootscript in my signature. Come back to the thread open a reply click on the **#** and paste all the text from the generated file between the code tags.

---

### Post by warda on 2010-11-26
hi and thanks for helping

please see the script results..


```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Syslinux is installed in the MBR of /dev/sda
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #5 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /COMMAND.COM

sdb2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sdb3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:

sdb6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 4002 MB, 4002938880 bytes
68 heads, 3 sectors/track, 38324 cylinders, total 7818240 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *              8     7,818,239     7,818,232   b W95 FAT32


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders, total 117210240 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63       224,909       224,847  de Dell Utility
/dev/sdb2    *        224,910    91,743,713    91,518,804   7 HPFS/NTFS
/dev/sdb3         105,081,165   117,194,174    12,113,010   7 HPFS/NTFS
/dev/sdb4          91,744,254   105,080,831    13,336,578   5 Extended
/dev/sdb5          91,744,256   104,400,895    12,656,640  83 Linux
/dev/sdb6         104,402,944   105,080,831       677,888  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        B8A8-CAAB                              vfat                             
/dev/sda: PTTYPE="dos" 
/dev/sdb1        07D7-0504                              vfat       DellUtility                   
/dev/sdb2        F4180C48180C0C74                       ntfs                                     
/dev/sdb3        9A80430F8042F175                       ntfs       Disk 2                        
/dev/sdb4: PTTYPE="dos" 
/dev/sdb5        ad0534fb-ad50-4e8c-a19a-066e9009bdf3   ext4                                     
/dev/sdb6        ae9cfcd2-2c6f-446e-ae85-5e0d309ed1bd   swap                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sda1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb2        /media/F4180C48180C0C74  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)

=============================== StdErr Messages: ===============================

/home/ubuntu/Desktop/boot_info_script055.sh: line 892:  5671 Killed                  mount -r -t "$type" $part "$mountname" 2>> $Mount_Error


```

---

### Post by wilee-nilee on 2010-11-26
Is that all the text from that file your missing some key parts.

Using the live Ubuntu cd run the bootscript in my signature. Come back to the thread open a reply click on the **#** and paste [COLOR="Red"]all[/COLOR] the text from the generated file between the code tags.

---

### Post by warda on 2010-11-27
hi,
thats all what is in the results file

i just open it, go select all and copy and paste...

any ideas at all?

thanks

```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Syslinux is installed in the MBR of /dev/sda
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #5 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /COMMAND.COM

sdb2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sdb3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:

sdb6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 4002 MB, 4002938880 bytes
68 heads, 3 sectors/track, 38324 cylinders, total 7818240 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *              8     7,818,239     7,818,232   b W95 FAT32


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders, total 117210240 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63       224,909       224,847  de Dell Utility
/dev/sdb2    *        224,910    91,743,713    91,518,804   7 HPFS/NTFS
/dev/sdb3         105,081,165   117,194,174    12,113,010   7 HPFS/NTFS
/dev/sdb4          91,744,254   105,080,831    13,336,578   5 Extended
/dev/sdb5          91,744,256   104,400,895    12,656,640  83 Linux
/dev/sdb6         104,402,944   105,080,831       677,888  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        B8A8-CAAB                              vfat       ANDRZEJ                       
/dev/sda: PTTYPE="dos" 
/dev/sdb1        07D7-0504                              vfat       DellUtility                   
/dev/sdb2        F4180C48180C0C74                       ntfs                                     
/dev/sdb3        9A80430F8042F175                       ntfs       Disk 2                        
/dev/sdb4: PTTYPE="dos" 
/dev/sdb5        ad0534fb-ad50-4e8c-a19a-066e9009bdf3   ext4                                     
/dev/sdb6        ae9cfcd2-2c6f-446e-ae85-5e0d309ed1bd   swap                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sda1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb2        /media/F4180C48180C0C74  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)

=============================== StdErr Messages: ===============================

/home/ubuntu/Desktop/boot_info_script055.sh: line 892:  4193 Killed                  mount -r -t "$type" $part "$mountname" 2>> $Mount_Error

```

---

### Post by warda on 2010-11-27
is it that after 9.04 failed and I was trying install 10.10 this process messed up partitions?

---

### Post by warda on 2010-11-29
hi can anyone help wtih this please?
wilee-nilee, can you tell how to fix it or what possibly is wrong? 
if no solution can i ask how to remove dual boot window so it will go streight into vista instead as it used to?
 
thank you

---

### Post by warda on 2010-11-30
hi everyone, looks no-one has idea how to help however I have managed finally to sort it out.

here are things I ve done if someone else will run in same kind of problems though they cumbersome and not to be considered as the solution. try on your own risk if nothing else work - just be sure to have backup first if you have any data on linux partition.

1. have formated partition for linux using vista
2. have used vista instal disk to remove grub loader
3. have tried install fedora instead (really determinated to try linux huh? :))
4. didnt work as fedora needs 10 GB disk space
5. this broke the boot though so again used vista inst disk to restore mbr
6. using vista reinstalling live usb on pendrive using Universal-USB-Installer-1.8.1.5.exe
7. booted from usb and it finally installed ubuntu 10.10 on y system.
I have after that also run all updates ad is working so far...

I realise that this is not professional solution but since one was not offered so far at least it worked ..

perhaps formating and restoring fixed problem whatever it was :)

good day everyone :)

im gonna have :popcorn: :)

---

### Post by misfitpierce on 2010-11-30
I just saw this post but good to see you got it working atm... Glad to hear it.

---

