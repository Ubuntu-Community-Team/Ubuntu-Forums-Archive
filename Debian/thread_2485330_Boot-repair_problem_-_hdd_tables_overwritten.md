---
title: "Boot-repair problem - hdd tables overwritten?"
date: 2023-03-27
forum: Debian
---

### Post by owenh2 on 2023-03-27
Help! Relative noob, Acer Aspire ES15 laptop with original Win 10 os.  
I shrank the original partitions on the laptop 1Tb hdd and have tried several flavours of Linux, the last being Debian 11, in the "new" partitions.  
After the latest Win 10 update I lost the grub menu so I loaded a live Debian 11 usb and ran boot-repair.  This became unresponsive after the first try 
- after the first "evaluation".  I rebooted, and it booted straight into a session labelled "boot repair".  It behaved like a Debian install, 
and I went along with the on-screen prompts until it asked about partitioning the hdd: I had 8 partitions between windows and linux, so I stopped 
there to consider my options.  The cursor suddenly came to life and started highlighting various options. I found the keyboard and mouse 
unresponsive, so shut down using the power button.  I am left with the report below.  No bootable partition reported, and an unwanted "lvm2" and 
"HOME-vg" volume group.

Here are (rough) notes I had on the hard drive structure just before the above events:
FROM        TO            LABEL    NOTES
```
start             206847    sda1    EFI
    206848        239615    sda2    MS reserved
    239616     921839615    sda3    boot mgr + MS Windows
 921839616     980433365    sda4    Linux MX17 + grub.efi
 980434944    1039026175    sda6    Linux  + grub.efi   
1039026176    1950496767    sda8    Linux
1950496768    1952497663    sda7    Linux-swap
1952497664    1953521663    sda5    Windows Recovery
```


```
BOOT-REPAIR SUMMARY

boot-repair-4ppa2056                                              [20230327_1413]

============================== Boot Info Summary ===============================

 => Grub2 (v1.99-2.00) is installed in the MBR of /dev/sda and looks at sector 
    1182169448 of the same hard drive for core.img, but core.img can not be 
    found at this location.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows 8/10/11/2012: FAT32
    Boot sector info:  According to the info in the boot sector, sda1 has 
                       204800 sectors.. But according to the info from the 
                       partition table, it has 1048575 sectors.
    Operating System:  
    Boot files:        /efi/Boot/bkpbootx64.efi /efi/Boot/bootx64.efi 
                       /efi/Boot/grubx64.efi /efi/LICK/HashTool.efi 
                       /efi/LICK/loader.efi /efi/LICK/shim.efi 
                       /efi/debian/fbx64.efi /efi/debian/grubx64.efi 
                       /efi/debian/mmx64.efi /efi/debian/shimx64.efi 
                       /efi/grub2win/gnugrub.kernel64.efi /efi/mx/grubx64.efi 
                       /efi/debian/grub.cfg /efi/Microsoft/Boot/bootmgfw.efi 
                       /efi/Microsoft/Boot/bootmgr.efi 
                       /efi/OEM/Boot/bootmgfw.efi /efi/OEM/Boot/bootmgr.efi

sda2: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info: 

sda3: __________________________________________________________________________

    File system:       LVM2_member
    Boot sector type:  -
    Boot sector info: 

sdb: ___________________________________________________________________________

    File system:       iso9660
    Boot sector type:  Grub2 (v1.99-2.00)
    Boot sector info:  Grub2 (v1.99-2.00) is installed in the boot sector of 
                       sdb and looks at sector 0 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Mounting failed:   mount: /mnt/BootInfo/FD/sdb: /dev/sdb already mounted or mount point busy.


================================ 0 OS detected =================================


================================ Host/Hardware =================================

CPU architecture: 64-bit
Video: Mullins [Radeon R4/R5 Graphics] from Advanced Micro Devices, Inc. [AMD/ATI]
Live-session OS is Ubuntu 64-bit (Ubuntu 22.04.2 LTS, jammy, x86_64)

===================================== UEFI =====================================

BIOS/UEFI firmware: V1.07(1.7) from Insyde Corp.
The firmware is EFI-compatible, and is set in EFI-mode for this live-session.
SecureBoot enabled.
BootCurrent: 0000
Timeout: 0 seconds
BootOrder: 2001,2002,2003
Boot0000* USB HDD: TDK    PciRoot(0x0)/Pci(0x10,0x0)/USB(2,0)/HD(2,GPT,7d4814d8-aaef-4505-8159-bee73d3422d2,0x54d1b0,0x2754)RC
Boot2001* EFI USB Device    RC
Boot2002* EFI DVD/CDROM    RC
Boot2003* EFI Network    RC

20ac8dde00311476f3755604eb0e545a   sda1/Boot/bkpbootx64.efi
cefed90870185ef689f004e686de8fce   sda1/Boot/bootx64.efi
8af5de47338c2010714ee8dbd7bc5c2f   sda1/Boot/grubx64.efi
45639d23aa5f2a394b03a65fc732acf2   sda1/LICK/HashTool.efi
80504e13bffc98ba52c0d8812896e759   sda1/LICK/loader.efi
4f7a4f566781869d252a09dc84923a82   sda1/LICK/shim.efi
0d240e1ce1b2b02dec9bbb162cfb94da   sda1/debian/fbx64.efi
8af5de47338c2010714ee8dbd7bc5c2f   sda1/debian/grubx64.efi
f617c3c1b1bdf56909dcb8e1b996749b   sda1/debian/mmx64.efi
cefed90870185ef689f004e686de8fce   sda1/debian/shimx64.efi
adc299d35076246d7abd3f20b747cd0d   sda1/grub2win/gnugrub.kernel64.efi
edc58aa3aff41833feaede870e8a006e   sda1/mx/grubx64.efi
20ac8dde00311476f3755604eb0e545a   sda1/Microsoft/Boot/bootmgfw.efi
27d382c5fc21df6f4a75baed05aa1d9d   sda1/Microsoft/Boot/bootmgr.efi
5260071ec03f7afc96a180c5442d4477   sda1/OEM/Boot/bootmgfw.efi
6f2ef9daa28804a29400d01627aa063c   sda1/OEM/Boot/bootmgr.efi

============================= Drive/Partition Info =============================

Disks info: ____________________________________________________________________

sda    : is-GPT,    no-BIOSboot,    has-noESP,     not-usb,    not-mmc, no-os,    no-wind,    2048 sectors * 512 bytes

Partitions info (1/3): _________________________________________________________

sda1    : no-os,    64, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    not-far
sda2    : no-os,    64, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    not-far

Partitions info (2/3): _________________________________________________________

sda1    : isnotESP,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot
sda2    : isnotESP,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot

Partitions info (3/3): _________________________________________________________

sda1    : not--sepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    sda
sda2    : maybesepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    sda

fdisk -l (filtered): ___________________________________________________________

Disk sda: 931.51 GiB, 1000204886016 bytes, 1953525168 sectors
Disk identifier: 119A9CA5-A89A-41DA-B185-1D8E1DA0D474
        Start        End    Sectors   Size Type
sda1     2048    1050623    1048576   512M Linux filesystem
sda2  1050624    2050047     999424   488M Linux filesystem
sda3  2050048 1953523711 1951473664 930.5G Linux LVM
Disk sdb: 3.73 GiB, 4004511744 bytes, 7821312 sectors
Disk identifier: 7D4814D8-AAEF-4505-815B-BEE73D3422D2
        Start     End Sectors  Size Type
sdb1       64 5558703 5558640  2.7G Microsoft basic data
sdb2  5558704 5568771   10068  4.9M EFI System
sdb3  5568772 5569371     600  300K Microsoft basic data
sdb4  5570560 7821248 2250689  1.1G Linux filesystem
Disk zram0: 2.39 GiB, 2561302528 bytes, 625318 sectors

parted -lm (filtered): _________________________________________________________

sda:1000GB:scsi:512:4096:gpt:ATA WDC WD10JPVX-22J:;
1:1049kB:538MB:537MB:fat32::;
2:538MB:1050MB:512MB:::;
3:1050MB:1000GB:999GB:::lvm;
sdb:4005MB:scsi:512:512:gpt:TDK :;
1:32.8kB:2846MB:2846MB::ISO9660:hidden, msftdata;
2:2846MB:2851MB:5155kB::Appended2:boot, esp;
3:2851MB:2852MB:307kB::Gap1:hidden, msftdata;
4:2852MB:4004MB:1152MB:ext4::;

blkid (filtered): ______________________________________________________________

NAME   FSTYPE      UUID                                   PARTUUID                             LABEL                     PARTLABEL
sda                                                                                                                      
&#9500;&#9472;sda1 vfat        D49C-E0B2                              2c9967a2-086a-43a4-954c-13edbf7216d9 ESP                       
&#9500;&#9472;sda2                                                    9ad7e6ad-15d4-47e3-8577-1793c86897e8                           
&#9492;&#9472;sda3 LVM2_member BwGV2L-usiW-Lwtr-Fu62-RLEn-cAzE-1dkodE 00eafa08-1f7d-4dc2-9f07-c1bf2b81f545                           
sdb    iso9660     2023-02-17-16-11-32-00                                                      Lubuntu 22.04.2 LTS amd64 
&#9500;&#9472;sdb1 iso9660     2023-02-17-16-11-32-00                 7d4814d8-aaef-4505-815a-bee73d3422d2 Lubuntu 22.04.2 LTS amd64 ISO9660
&#9500;&#9472;sdb2 vfat        F7DB-4D56                              7d4814d8-aaef-4505-8159-bee73d3422d2 ESP                       Appended2
&#9500;&#9472;sdb3                                                    7d4814d8-aaef-4505-8158-bee73d3422d2                           Gap1
&#9492;&#9472;sdb4 ext4        00e82163-9485-4210-8176-ceb4942f5631   112e37c0-a027-b34c-9ae3-d892ed5a0916 writable                  

Mount points (filtered): _______________________________________________________

                                                               Avail Use% Mounted on
/dev/disk/by-label/writable[/install-logs-2023-03-27.0/crash] 974.3M   0% /var/crash
/dev/disk/by-label/writable[/install-logs-2023-03-27.0/log]   974.3M   0% /var/log
/dev/sda1                                                      31.4M  67% /mnt/boot-sav/sda1
/dev/sdb1                                                          0 100% /cdrom

Mount options (filtered): ______________________________________________________


===================== sda1/efi/debian/grub.cfg (filtered) ======================

search.fs_uuid 7a6661f3-c920-4d47-9a46-d07d10774d03 root hd0,gpt8 
set prefix=($root)'/grub'
configfile $prefix/grub.cfg


==================== blkid (filtered) before lvm activation ====================

/dev/sda1: LABEL_FATBOOT="ESP" LABEL="ESP" UUID="D49C-E0B2" BLOCK_SIZE="512" TYPE="vfat" PARTUUID="2c9967a2-086a-43a4-954c-13edbf7216d9"
/dev/sdb1: BLOCK_SIZE="2048" UUID="2023-02-17-16-11-32-00" LABEL="Lubuntu 22.04.2 LTS amd64" TYPE="iso9660" PARTLABEL="ISO9660" PARTUUID="7d4814d8-aaef-4505-815a-bee73d3422d2"
/dev/sdb4: LABEL="writable" UUID="00e82163-9485-4210-8176-ceb4942f5631" BLOCK_SIZE="4096" TYPE="ext4" PARTUUID="112e37c0-a027-b34c-9ae3-d892ed5a0916"
/dev/sdb2: SEC_TYPE="msdos" LABEL_FATBOOT="ESP" LABEL="ESP" UUID="F7DB-4D56" BLOCK_SIZE="512" TYPE="vfat" PARTLABEL="Appended2" PARTUUID="7d4814d8-aaef-4505-8159-bee73d3422d2"
/dev/sda3: UUID="BwGV2L-usiW-Lwtr-Fu62-RLEn-cAzE-1dkodE" TYPE="LVM2_member" PARTUUID="00eafa08-1f7d-4dc2-9f07-c1bf2b81f545"
/dev/zram0: UUID="bdd6e139-e3f5-4081-a00a-1e80acf0ed9d" TYPE="swap"
/dev/sdb3: PARTLABEL="Gap1" PARTUUID="7d4814d8-aaef-4505-8158-bee73d3422d2"
/dev/sda2: PARTUUID="9ad7e6ad-15d4-47e3-8577-1793c86897e8"


================================ LVM activation ================================

modprobe dm-mod  
vgscan --mknodes
  Found volume group "HOME-vg" using metadata type lvm2
vgchange -ay
  0 logical volume(s) in volume group "HOME-vg" now active
lvscan

blkid -g



Suggested repair: ______________________________________________________________

The default repair of the Boot-Repair utility would not act on the boot.
```

---

### Post by oldfred on 2023-03-27
Moved to Debian sub-forum, since not Ubuntu.
Edited to add code tags.

How to use Code tags, # in Forum's advanced editor
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)
[http://ubuntuforums.org/showthread.php?p=12776168#post12776168](http://ubuntuforums.org/showthread.php?p=12776168#post12776168)

You cannot mix BIOS install of grub with UEFI install of grub. You need to always boot in UEFI mode.
Boot-Repair would not have changed partitions, that requires gparted or other partition tools.
It looks like sda1 is not now ESP, use gparted to change to esp,boot.
Difficult to remove grub from gpt's protective MBR, so we leave it and just never try to boot in BIOS/CSM/Legacy mode.
You have to choose boot mode each time you boot a live installer or repair drive. UEFI has a default setting that applies to installed systems.

I do not know LVM nor win2grub which may complicate issues.
I do know you have to mount the LVM to reinstall grub as it has to see / inside the volumes.

Not sure if differences with Debian over Ubuntu.
chroot with UEFI, LVM, encryption on NVMe drive
[https://ubuntuforums.org/showthread.php?t=2349833&p=13602088#post13602088](https://ubuntuforums.org/showthread.php?t=2349833&p=13602088#post13602088)
To chroot, you need the same 32bit or 64 bit kernel. Best to use same version.
[https://help.ubuntu.com/community/BasicChroot](https://help.ubuntu.com/community/BasicChroot)

---

### Post by owenh2 on 2023-04-15
Thanks for the reply, and sorry for the delay.  Only back online now, on a Lubuntu live usb boot.  I've been checking some of the points in the reply:
1. No mixing BIOS and EFI - all was EFI: the Debian live usb; original PC system and the current usb
2. I did not recognise the difference between running boot-repair and trying to reinstall Debian - the splash at startup had a Boot-Repair label!
3. I became suspicious on the second run when the menu choices looked like an install; I paused to think, and to check I had my notes on what the HDD partitioning looked like 
4. During this pause, with no input (?) the screen came to life: choices which vanished too quickly for me to take them in came and went.  When it was obvious to me that I could not affect the inputs, I powered down (i.e. held down the power switch for several seconds.  One of the last screen changes I saw was a dialogue warning of the changes a LVM would make.

Looking at the (unresponsive and unbootable) HDD now from a Lubuntu live USB boot, gdisk shows a couple of small unlabeled partitions with no readable features, plus one large (930GB) equally featureless partition.  

I tried extracting data from the MBR, but there was only one partition for the whole HDD.

Any ideas? Can I recreate any structure from the NOTES (top of original post).  I would like to rescue the first 3 partitions to get Windows back as that's where all my data is (I copied work done in Linux to the Windows partition)

Thanks for reading such a long rambling post

---

### Post by oldfred on 2023-04-15
You have grub in MBR, so at least once you reinstalled grub in BIOS mode.
Since UEFI only boot in UEFI mode.

With Ubuntu when installing with Something Else, it has to scan partitions. I have lots of partitions on two drives, so sometimes it takes a bit before it responds.

You have LVM in sda3. I do not use LVM. Is it also encrypted?
Boot-Repair has trouble telling LVM from RAID, so if it sees it then it will ask if you have RAID. But Boot-Repair's main fix is grub-update or total reinstall of grub. It does not change partitions. It may offer to run fsck.

While many here in forum suggest LVM, I think it is more for experienced users. But if you want full drive encryption, you use LVM and then have jumped into the deep end of the pool to learn to swim.

Mount LVM - duckhook
[https://ubuntuforums.org/showthread.php?t=2383017&p=13733372#post13733372](https://ubuntuforums.org/showthread.php?t=2383017&p=13733372#post13733372)
[https://unix.stackexchange.com/questions/339011/how-do-i-mount-an-lvm-partition/339621#339621](https://unix.stackexchange.com/questions/339011/how-do-i-mount-an-lvm-partition/339621#339621)
For mounting encrypted see first few lines:
[https://askubuntu.com/questions/262211/how-do-i-resize-an-encrypted-lvm-to-install-another-copy-of-ubuntu](https://askubuntu.com/questions/262211/how-do-i-resize-an-encrypted-lvm-to-install-another-copy-of-ubuntu)

If you do not have good backups mount LVM and backup your data.

---

### Post by owenh2 on 2023-04-15
Thanks for quick reply.  
I know nothing about LVM and do not want it.  I assume that's what was being installed when I was trying to switch the laptop off.  I have tried various linux flavours, so must have made a mistake somewhere and used BIOS boot whilst installing - I have a recollection of trying Antix with a peculiar installation package using its own live usb creator in windows.  It never worked, but that may have been the BIOS boot :(

If it has repartitioned the HDD, I wonder if I can rewrite the GPT tables to at least get the first three recognisable as Windows, and then add ubuntu in a final set of partitions.  Any ideas would br helpful

---

### Post by oldfred on 2023-04-15
What does testdisk show? If deeper search shows files immediately back them up. Some later never can get them again.

[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery) & 
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

repairs including testdisk info & links
[https://help.ubuntu.com/community/DataRecovery#Lost_Partition](https://help.ubuntu.com/community/DataRecovery#Lost_Partition)
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

I doubt you can get everything back, it looks like you have overwritten data.

You then can try photorec.
[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec) & 
[http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step](http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step)
[http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)

---

