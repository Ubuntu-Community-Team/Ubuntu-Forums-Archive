---
title: "Windows 7 SP1 Install Fails with Ubuntu Dual Boot"
date: 2014-12-28
forum: Desktop Environments
---

### Post by kingkratos on 2014-12-28
I have dual boot set up with Windows 7 and Ubuntu 14.04. Windows has SP1 update available, but it continues to fail with [COLOR=#333333][FONT=Segoe UI]error 0x800F0A12. Upon researching this error, I believe that this update will not install because I am dual booting with grub, but the update is requiring only one boot system (Windows). 

How can I safely change the default boot to Windows (from what I have read, MS is calling this making Windows boot "Active") to install this update and then change back to grub to dual boot like normal without having to re-install Ubuntu?

This is what I have for partitions. As you can see, my small sda1 is currently the boot location.

[/FONT][/COLOR]```
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63      208844      104391   de  Dell Utility
/dev/sda2          208845    30928844    15360000    7  HPFS/NTFS/exFAT
/dev/sda3        30928845   840651439   404861297+   7  HPFS/NTFS/exFAT
/dev/sda4       840652798  1250263039   204805121    5  Extended
/dev/sda5       840652800   893900846    26624023+  83  Linux
/dev/sda6       893902848  1238095871   172096512   83  Linux
/dev/sda7      1238097920  1250263039     6082560   82  Linux swap / Solaris



```[COLOR=#333333][FONT=Segoe UI]

Please help me figure this out as I would like to install the Windows update to keep my system current, but do not want to kill my Ubuntu system.

Kratos[/FONT][/COLOR]

---

### Post by yancek on 2014-12-28
You could go to the site below and download and run the boot repair selecting to get bootinfo summary report and posting it here.  Are you sure the first partition has boot files on it as it is labelled "Dell Utility".  I would think it would be sda2 or sda3 but I've never used a Dell so...?

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by kingkratos on 2014-12-28
I will run that later today and post the summary. 

As for whether the Dell Utility labeled partition actually has boot info or not, i am not sure. When I first installed Ubuntu a few years ago, I cannot remember which partition was flagged as boot. I do know that gparted has this partition flagged as boot, so i just assumed it was the a boot partition.

Kratos

---

### Post by dreamer2 on 2014-12-28
Failure to update in windows is sometimes due to RPC and related services being shut down. Check Windows services. If windows and ubuntu both boot. It might be a Windows remote procedure call problem or space issue.

Just sayin',
Gary

---

### Post by kingkratos on 2014-12-28
I know for sure it is not a space issue as I have plenty of space on all of my partitions. I can install all other updates in Windows, except SP1. In reading about that error code, I can see that it definitely has something to do with Windows not being the default boot, or something like that.

Here is the boot info,

```

[COLOR=#666666]=============================[/COLOR][COLOR=#000000] Boot Info Summary: [/COLOR][COLOR=#666666]===============================[/COLOR]
 [COLOR=#666666]=[/COLOR]> Grub2 [COLOR=#666666]([/COLOR]v2.00[COLOR=#666666])[/COLOR] is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive [COLOR=#AA22FF]**for **[/COLOR]core.img. core.img is at this location and looks 
    [COLOR=#AA22FF]**for**[/COLOR] [COLOR=#666666]([/COLOR],msdos5[COLOR=#666666])[/COLOR]/boot/grub.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector [COLOR=#AA22FF]type[/COLOR]:  Grub2 [COLOR=#666666]([/COLOR]v1.99-2.00[COLOR=#666666])[/COLOR]
    Boot sector info:  Grub2 [COLOR=#666666]([/COLOR]v2.00[COLOR=#666666])[/COLOR] is installed in the boot sector of sda1 
                       and looks at sector 858188592 of the same hard drive 
                       [COLOR=#AA22FF]**for **[/COLOR]core.img. core.img is at this location and looks 
                       [COLOR=#AA22FF]**for**[/COLOR] [COLOR=#666666]([/COLOR],msdos5[COLOR=#666666])[/COLOR]/boot/grub. No errors found in the Boot 
                       Parameter Block.
    Operating System:  
    Boot files:        /DELLBIO.BIN /DELLRMK.BIN /COMMAND.COM

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector [COLOR=#AA22FF]type[/COLOR]:  Windows 7/2008: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector [COLOR=#AA22FF]type[/COLOR]:  Windows Vista: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector [COLOR=#AA22FF]type[/COLOR]:  -
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector [COLOR=#AA22FF]type[/COLOR]:  -
    Boot sector info: 
    Operating System:  Ubuntu 14.04.1 LTS 
    Boot files:        /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/i386-pc/core.img

sda6: __________________________________________________________________________

    File system:       ext4
    Boot sector [COLOR=#AA22FF]type[/COLOR]:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sda7: __________________________________________________________________________

    File system:       
    Boot sector [COLOR=#AA22FF]type[/COLOR]:  -
    Boot sector info:  [COLOR=#000000]    Mounting failed:   mount: unknown filesystem [/COLOR][COLOR=#AA22FF]type[/COLOR][COLOR=#BB4444]''[/COLOR]
```

It also has this at the very bottom of the summary:

```
[COLOR=#666666]===================[/COLOR][COLOR=#000000] Suggested repair[/COLOR]The default repair of the Boot-Repair utility would reinstall the grub2 of sda5 into the MBR of sda.
Additional repair would be performed: unhide-bootmenu-10s   fix-windows-boot


[COLOR=#666666]===================[/COLOR] Final advice in [COLOR=#AA22FF]**case **[/COLOR]of suggested repair


The boot files of [COLOR=#666666][[/COLOR]The OS now in use - Ubuntu 14.04.1 LTS[COLOR=#666666]][/COLOR] are far from the start of the disk. Your BIOS may not detect them. You may want to retry after creating a /boot partition [COLOR=#666666]([/COLOR]EXT4, >200MB, start of the disk[COLOR=#666666])[/COLOR]. This can be performed via tools such as gParted. Then [COLOR=#AA22FF]**select **[/COLOR]this partition via the [COLOR=#666666][[/COLOR]Separate /boot partition:[COLOR=#666666]][/COLOR] option of [COLOR=#666666][[/COLOR]Boot Repair[COLOR=#666666]][/COLOR]. [COLOR=#666666]([/COLOR]https://help.ubuntu.com/community/BootPartition[COLOR=#666666])[/COLOR]


[COLOR=#666666]===================[/COLOR] User settings [COLOR=#000000]The settings chosen by the user will not act on the boot.[/COLOR]
```

Kratos

---

### Post by kingkratos on 2014-12-28
I ended up running the boot repair recommended repair utility and am currently trying to install the Windows 7 SP1 update. I will update with whether this worked or not later. I was able to boot into Windows just fine, but have not yet tried to boot to Ubuntu yet.

Kratos

---

### Post by oldfred on 2014-12-28
Boot flag definitely should be on sda2 as that is where Windows boot files are. Not sure if Boot-Repair moved them or not.
Grub does not use boot flag, so would boot Windows as it just looks for the Windows boot files. But Windows never would have booted with a Windows boot loader. And a Windows boot loader would have found grub in the partition boot sector of sda1 and just booted grub again.

You do have grub installed to the partition boot sector of sda1 which is FAT32. I know you cannot do that with NTFS as Windows has boot info in the partition boot sector. Not sure about FAT32. NTFS has a backup, not sure about FAT32, not exactly how to fix it, if it is an issue. The fix with NTFS is to use testdisk to restore from the partition sector backup.

---

### Post by kingkratos on 2014-12-28
Ok. So boot repair didn't work. I tried seeing the active flag to the "c" partition.  When I view the partitions with gparted now, it shows that the "c" partition, or Windows partition is the boot partition. 

I did notice also that the Dell utilities partition is flagged as diag. So I think that means diagnostics? 

Anyway, I'm going to try to install again since setting "c" as active. Will  post  again with update. 

If anyone had other suggestions please let me know. 

Kratos

---

### Post by oldfred on 2014-12-28
The sda2 partition has the boot files, so must have boot flag.
Boot files:        /bootmgr /Boot/BCD

---

### Post by kingkratos on 2014-12-29
sda2 is my system recovery (factory) partition. Would it make sense to have the factory image partition be the primary boot for Windows?

I tried installing SP1 again and it still fails. You think changing sda2 to have the boot flag would work?

Kratos

---

### Post by oldfred on 2014-12-29
If sda2 is really recovery partition what happened to Windows boot partition? It usually is a 100MB partition just with the boot files bootmgr & BCD that you show in sda2.
And sda3 does not have them. You can put boot flag on sda3, but must then add bootmgr & create a BCD. If sda2 is a recovery the BCD will not include boot of Windows, so you cannot copy it. You may be able to copy bootmgr as I think it is the same.
You then need to use Windows repair CD or flash drive to add bootmgr & create a new BCD to directly boot Windows. You do not have to have the separater 100MB boot partition that is common with Windows 7.

Then boot flag must be on sda3, for both repairs & updates.

---

