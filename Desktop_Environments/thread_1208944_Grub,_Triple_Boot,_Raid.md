---
title: "Grub, Triple Boot, Raid?"
date: 2009-07-09
forum: Desktop Environments
---

### Post by drtydogg on 2009-07-09
I have been running a triple boot system for a couple of months now with the following setup.

HD1 Windows
HD2/0 Ubuntu
HD2/1 OS X

recently I purchased a couple of new hard drives and installed them in RAID 0 to test out Windows 7.  Now though whenever I turn on the HDs in RAID the Grub Menu never shows.  If I set the computer to boot from HD2 first, where Grub is installed, it goes straight to the Darwin boot loader.  If I unplug on of the RAID drives causing the RAID setup to fail, then Grub shows just as normal.  Is there a way to have grub still work with RAID on a system?

Thanks in advance,
[COLOR="Gray"]Donnie[/COLOR]

---

### Post by NewbieNik on 2009-07-10
Is this RAID a dedicated controller, an on-board RAID (Such as nVidia chipsets) or a software RAID as found in Ubuntu installation?
It doesn't explain everything, but if you have a software RAID controller then the BIOS cannot see the RAID array and therefore none of the boot data on it. I have seen this error affect other drives not RAID'd on the same box.
If you have a dedicated RAID controller then post the make and model and drive configuration and we'' see if we can help.

---

### Post by drtydogg on 2009-07-12
Thanks for the reply, the raid array is running on the integrated Intel ICH10R chipset.  The Hard drive that contains Grub/Ubuntu is actually running on a secondary controller I believe it's based on a Marvel chipset, and that is set to ACHI.  I'll have to look that up, the board is a Gigabyte P45-UD3R.

---

### Post by nisals on 2009-07-15
Hello
I have been trying to triple boot with XP, Vista and Ubuntu. I have installed XP first, then Vista then Ubuntu. But after all installations i can only access Vista and Ubuntu. on Grub it doenst show my XP, it just says other operating systems and VIsta below it.
i have ran the boot_info_script on ubuntu and here is my result.txt
any help is appreciated.. thank you


============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #6 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Syslinux is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  Windows XP
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x2798225e

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   368,643,554   368,643,492   7 HPFS/NTFS
/dev/sda2         368,643,555   625,121,279   256,477,725   f W95 Ext d (LBA)
/dev/sda5         368,643,618   593,923,049   225,279,432   7 HPFS/NTFS
/dev/sda6         593,923,113   618,502,499    24,579,387  83 Linux
/dev/sda7         618,502,563   625,121,279     6,618,717  82 Linux swap / Solaris


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 8029 MB, 8029470208 bytes
255 heads, 63 sectors/track, 976 cylinders, total 15682559 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00037ac6

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63    15,679,439    15,679,377   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="2C1A6A9A1A6A6136" LABEL="S3A6747D002" TYPE="ntfs" 
/dev/sda5: UUID="48C8F554C8F5412C" TYPE="ntfs" 
/dev/sda6: UUID="46492a12-7695-42c8-b282-984b495936fd" TYPE="ext3" 
/dev/sda7: UUID="9281578e-90df-4ba5-9070-95d34151ad67" TYPE="swap" 
/dev/sdc1: UUID="49DF-920E" TYPE="vfat"

---

### Post by drtydogg on 2009-07-15
you are going to have to manually edit the /boot/grub/menu.lst file to add an entry for Windows XP.  You are going to need to add something like this to below the Vista entry:

title Windows XP
root (hd0,4)
savedefault
makeactive
chainloader +1

---

