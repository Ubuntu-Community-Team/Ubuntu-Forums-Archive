---
title: "installing lubuntu alongside windows 7"
date: 2014-05-16
forum: Debian
---

### Post by raffa2 on 2014-05-16
hi everyone. here's the big summary: i now have both lubuntu 14.04 and windows 7 installed on my laptop. i had booting problems, so used boot-repair. boot-repair installed grub and now i can enter lubuntu just fine. but at first, when i tried to load windows 7 loader it said it couldn't find the right efi file path. then i ran boot-repair again and now i only have two choices while booting: lubuntu or windows boot manager. but windows boot manager just makes the screen go black for a few seconds and goes right back to grub again...

here's the boot-repair stuff from the second time i ran it:

[http://paste.ubuntu.com/7476041/](http://paste.ubuntu.com/7476041/)

i hope someone can help me. this is all a bit overwhelming.

---

### Post by oldfred on 2014-05-17
You have an UEFI system, but installed Lubuntu in BIOS boot mode. The two boot modes are not compatible and you cannot dual boot from grub menu as once you start booting in one mode you cannot change to other mode. But can dual boot from UEFI menu or one time boot key.

But Boot-Repair converted your Lubuntu install to UEFI boot. But you must of run it several times as it offered its 'buggy' UEFI fix.

       Boot_Repair - Always say no until proven that you only can boot Windows entry from UEFI menu.
buggy-kernel detected. Do you want to activate [Backup and rename Windows EFI files]? yes (if any choice fails, please retry with the other)
To undo & to rename files to their original names, you just need to tick the "Restore EFI backups" option of Boot-Repair.

Because of the rename, you actually boot grub from Windows entry in UEFI. But I do not see that Boot-Repair added its entry and the os-prober entry just then links back to Windows which is still grub.


```
 BootOrder: 0000,0001,0003,0002
Boot0000* Windows Boot Manager    HD(1,800,64000,584df351-a471-44ab-a90b-c12c90007879)File(EFIMicrosoftBootbootmgfw.efi)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}....................
Boot0001* ubuntu    HD(1,800,64000,584df351-a471-44ab-a90b-c12c90007879)File(EFIubuntu[COLOR=#ff0000]shimx64.efi[/COLOR])
Boot0002  CD/DVD Drive     BIOS(3,0,00)AMGOAMNO........o.S.l.i.m.t.y.p.e. .D.V.D. .A. . .D.S.8.A.8.S.H....................A...........................>..Gd-.;.A..MQ..L.2.3.8.0.8.5. .3.A.6.2.6.4.1.0.4.7.1.3.8......AMBO
Boot0003* ubuntu    HD(1,800,64000,584df351-a471-44ab-a90b-c12c90007879)File(EFIUbuntu[COLOR=#ff0000]grubx64.efi[/COLOR])


```

First undo rename and test if you can boot from UEFI menu or one time boot key either ubuntu entry in UEFI boot menu. One is grub and the other shim for secure boot. Both should work if secure boot is off.

Also you must remove boot flag from sda3. With gpt partitioning and gparted the boot flag it to indicate which partition is the ESP or efi boot partition. It is not the same as the boot flag in BIOS which indicates which Windows partition is bootable. You can only have one partition with boot flag per hard drive.

You also installed grub to the PBR-partition boot sector of sda4. That means Windows will not see that partition as NTFS. It may show as RAW or unformatted as it does not have the correct NTFS signature. You should be able to restore a backup of the PBR with testdisk if you only wrote into it once.

Fix for most, a few have other issues, better than windows fix in many cases as it also fixes other parameters:
If win7 use small 'system reserved' NTFS partition instead of the partition where windows was installed for win7
This has instructions on using testdisk to repair the install of grub to the boot sector for windows from Ubuntu or Linux LiveCD.
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)
You want to get to this screen:
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery)

OR:
[HowTo] Repair the bootsector of a Windows partition  - YannBuntu
[https://help.ubuntu.com/community/BootSectorFix](https://help.ubuntu.com/community/BootSectorFix)
[http://ubuntuforums.org/showthread.php?t=1926510](http://ubuntuforums.org/showthread.php?t=1926510)

---

### Post by raffa2 on 2014-05-17
thank you for the answer! ok, here's what i did: first, i ran boot-repair once again but i ticked that little box that said "restore efi backup" now, windows 7 boots, but it stays on the "starting windows" screen forever.

when i tried following the tutorials using testdisk, there was no partition that said that the boot sector was bad. they were all ok and there was no "backup  BS option"

also i guess i should say that every time i run boot repair the final screen tells me an error happened.

here's a new boot info summary: [http://paste.ubuntu.com/7478900/](http://paste.ubuntu.com/7478900/)

hopefully you'll have patience with a dummy like me!

---

### Post by oldfred on 2014-05-17
While not recommended having grub in a PBR is perfectly valid, so Boot-Repair will not say it is wrong. But in a NTFS formatted partition it is wrong. It should say backup is different and let you restore from backup.

If you cannot restore from backup you have to use the Rebuild BS as that is the only way to get it seen as NTFS. Windows will not recreate a boot sector unless it is seen as NTS. The version testdisk creates I think is still the old XP type, which is different than the newer Vista/7/8 type. But once converted from grub to NTFS you can run chkdsk on the partition and it then should be fine.


I am not sure why Boot-Repair is showing an error. Often grub shows a reinstall with error  = 0 or no error and still Boot-Repair says it had an error. Not sure what it is picking up but many find it works so I have started ignoring error and just check if grub installed shows an error.

---

### Post by raffa2 on 2014-05-17
well, i selected rebuild bs but i'm not sure it did anything. how do i check if the partition is now ntfs?

---

### Post by oldfred on 2014-05-17
Run chkdsk on that partition.
Then post or review a new BootInfo report to see if the partition boot sector of sda4 now says NTFS like the main Windows partition.

---

### Post by raffa2 on 2014-05-17
well... here's the latest boot-info summary: [http://paste.ubuntu.com/7479536/](http://paste.ubuntu.com/7479536/)

i didn't know how to run chkdsk, so i googled and used fsck. here's what happens:


```
~$ sudo fsck /dev/sda4
fsck from util-linux 2.20.1
fsck: fsck.ntfs-3g: not found
fsck: error 2 while executing fsck.ntfs-3g for /dev/sda4
```

then i googled some more and discovered ntfsfix and ran it on sda4:

```
~$ sudo ntfsfix /dev/sda4
Mounting volume... OK
Processing of $MFT and $MFTMirr completed successfully.
Checking the alternate boot sector... OK
NTFS volume version is 3.1.
NTFS partition /dev/sda4 was processed successfully.

```


then for some reason i decided to run it on sda1 too and this happens:

```
~$ sudo ntfsfix /dev/sda1
Mounting volume... NTFS signature is missing.
FAILED
Attempting to correct errors... NTFS signature is missing.
FAILED
Failed to startup volume: Invalid argument
NTFS signature is missing.
Trying the alternate boot sector
NTFS signature is missing.
Unrecoverable error
Volume is corrupt. You should run chkdsk.

```

i don't know how to run chkdsk without windows! i'm not sure what to do and where the problem is. oh boy.

---

### Post by oldfred on 2014-05-17
I do not see that anything has changed? Is this a new BootInfo report or the old one?

You have to remove the boot flag from sda3, use gparted on live installer for that. Then Windows should boot from UEFI menu.

But did you run testdisk on sda4? It still has grub in PBR.

And you can only run chkdsk from Windows. Best to always have a Windows repairCD or flash drive.
the ntfsfix only does very minor changes and turns on the chkdsk flag.

You have to run the correct utility for checking file structure. From Windows you use chkdsk on NTFS or FAT.
From Linux your use e2fsck only on the ext2, ext3, or ext4 formats. 
You also can run a check on fat32 from Linux.
       sudo /sbin/fsck.vfat -V <the fat32 device>
or

 sudo dosfsck -t -a -w /dev/sdb1
See this for details:
man dosfsck

---

### Post by raffa2 on 2014-05-18
thank you so much! removing the boot flag on sda3 did the trick and now i can dual boot! yay! however, windows always runs chkdsk when it boots, so that sucks. but i'll figure something out. thanks again! i hope i'm one day as smart as you.

---

### Post by oldos2er on 2014-05-18
Could you please mark the thread as 'Solved' under Thread Tools at the top of the page? This will help others who might be having the same problem.

If you have more Lubuntu questions you can post them in the regular support areas of the forum since Lubuntu is part of the Ubuntu family.

---

