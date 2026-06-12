---
title: "Dual boot Windows 8 and Precise -Dell XPS 8500"
date: 2013-01-19
forum: Dell Ubuntu Support (CLOSED)
---

### Post by unconcrete on 2013-01-19
Recently, I've bought a Dell XPs 8500 64 bit an Win 8. First of all, i don't waste your time, so I precise that I have only basic skill about Linux, and some questions are well-known for most of you. Anyway, I ask your advice or a suggestion for a good tutorial.
I'd like to know how to dual boot Precise pangolin with Windows 8. I know 12.10 is more suitable for an UEFI system as XPS 8500 but for professional reasons it's necessary for me to install an LTS.
Now the problems.
Partitioning and Grub location.
-----------------------------------------
I'm used to install ubuntu from Dapper Drake in dual boot with Windows XP. Each time i've used gparted to resiza win partition and make room for ubuntu. Until now. You know i'me using a live-usb for Precise. 
First time Grparted warns me about the ntfs partition is inconsistent. Tip: chkdsk -f and reboot  2 times.
So I do. Nothing happens. The partition of ntfs /dev/sda5, drive c: label OS(ntfs) in windows terms is recognized by gparted but I can't modify it. I am confused by the various partitions Dell created for my system. In case it is useful I post some tests:
---------------------------------------------------------------------------------------------------
ubuntu@ubuntu:~$ sudo parted -l
Error: The backup GPT table is not at the end of the disk, as it should be.
This might mean that another operating system believes the disk is smaller.
Fix, by moving the backup to the end (and removing the old backup)?
Fix/Ignore/Cancel?
Warning: Not all of the space available to /dev/sda appears to be used, you can
fix the GPT to use all of the space (an extra 4521 blocks) or continue with the
current setting?
Fix/Ignore? ^C
Model: ATA ST2000DM001-1CH1 (scsi)
Disk /dev/sda: 2000GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt

Number Start End Size File system Name Flags
1 1049kB 525MB 524MB fat32 EFI system partition boot
2 528MB 570MB 41.9MB fat32 Basic data partition hidden
3 570MB 705MB 134MB Microsoft reserved partition msftres
4 705MB 1229MB 524MB ntfs Basic data partition hidden, diag
5 1229MB 1993GB 1992GB ntfs Basic data partition
6 1993GB 2000GB 7358MB ntfs Microsoft recovery partition hidden, diag
Error: /dev/sdb: unrecognised disk label

Model: SAMSUNG HD103SI (scsi)
Disk /dev/sdc: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Number Start End Size Type File system Flags
1 32.3kB 1000GB 1000GB primary fat32 lba

(external hard disks)
Model: Verbatim (scsi)
Disk /dev/sdd: 15.7GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Number Start End Size Type File system Flags
1 65.5kB 15.7GB 15.7GB primary fat32 boot, lba

Model: WD Ext HDD 1021 (scsi)
Disk /dev/sde: 3001GB
Sector size (logical/physical): 4096B/4096B
Partition Table: msdos

Number Start End Size Type File system Flags
1 1049kB 3001GB 3001GB primary

parted: write error
ubuntu@ubuntu:~$
--------------------------------------------------------------------------------------
sudo gdisk -l /dev/sda
Partition table scan:
MBR: protective
BSD: not present
APM: not present
GPT: present

Found valid GPT with protective MBR; using GPT.
Disk /dev/sda: 3907029168 sectors, 1.8 TiB
Logical sector size: 512 bytes
Disk identifier (GUID): 0FF7F015-4185-4E5A-8BBC-98945CDB443E
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 3907024613
Partitions will be aligned on 2048-sector boundaries
Total free space is 1921132477 sectors (916.1 GiB)

Number Start (sector) End (sector) Size Code Name
1 2048 1026047 500.0 MiB EF00 EFI system partition
2 1032192 1114111 40.0 MiB FFFF Basic data partition
3 1114112 1376255 128.0 MiB 0C01 Microsoft reserved part
4 1376256 2400255 500.0 MiB 2700 Basic data partition
5 2400256 1971529727 939.0 GiB 0700 Basic data partition
6 3892652032 3907022598 6.9 GiB 2700 Microsoft recovery part
ubuntu@ubuntu:~$
------------------------------
So I've tried to resize it from Win8, and now I have enough space for ubuntu. 
I have about 930 GB for Win and 916 for Ubuntu 8 (unallocated space).
I've used again gparted from usb and created a linux-sswap and an ext 4 journaling partitions. Even if i don't know why gparted put a (!) warning in front of my NTFS partition, the installation proceeds...until the install crashes because the default location for grub2 probably is not ready or fot other mistakes. 
Actually at reboot only Windows 8 works.
Some tips?
Thanks in advance,
Dini-Verdiani,
Firenze
Italy

---

### Post by oldfred on 2013-01-19
Because you have Windows 8 pre-installed you have secure boot. Currently only 12.10 has grub2 2.00 which supports secure boot. But 12.04 is getting a major update to kernel & grub with the next point release and will in effect have the same as 12.10. But because it is a large update it has been delayed to February.

It did not show sdb? Is this an UltraBook or similar system with Intel SRT. That uses RAID which confuses many standard partition tools.

You may be able to boot 12.04 in UEFI mode many have installed it with Windows 7 that did not have secure boot. And I have noticed some updated to grub 1.99 that mention secure boot so it may partially be updated already. 

You have to turn secure boot off, and turn off fast boot. If fast boot is left on the only way to get into UEFI/BIOS is thru Windows. And if you cannot boot Windows at some point you then cannot get into UEFI and are bricked. Ubuntu supposedly has released a fix, but again that is with 12.10.

       You will need to use the 64 bit version of 12.10 and from the UEFI menu boot the flash drive in UEFI mode. That way it will install in UEFI mode.
Systems need quick boot or fast boot turned off in UEFI settings. Vital for some systems.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)
[https://help.ubuntu.com/community/UEFIBooting](https://help.ubuntu.com/community/UEFIBooting)

       Dell XPS 8500, desktop. Win 8 eventually worked (Ignore sidetrack to EasyBCD)
[http://ubuntuforums.org/showthread.php?t=2086383](http://ubuntuforums.org/showthread.php?t=2086383)
No EFI boot on Dell Inspiron One 2330 UEFI/BIOS update solved issues:
[http://ubuntuforums.org/showthread.php?t=2086631](http://ubuntuforums.org/showthread.php?t=2086631)

             You cannot use the Win7 DVD in UEFI mode, you need to use BIOS mode or modify to USB with UEFI.
[http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD](http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD)
[http://software.intel.com/en-us/articles/efi-shells-and-scripting/](http://software.intel.com/en-us/articles/efi-shells-and-scripting/)

grub2's os-prober creates wrong style (BIOS) chain boot entry, but Boot-Repair can fix.
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383)
Type of entry that does not work:
'Windows ...) (on /dev/sdXY)'
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Always best to have repairCD or liveCD of the current version of every system you have installed.
       
 Windows 8 UEFI repair USB must be FAT32
[http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html](http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html)
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)

I would not create one large system partition for Ubuntu. For both Windows & Linux I suggest smaller system partitions and separate /home or data partitions. I use 25GB for all my Linux system partition and have large data partitions, one NTFS to share with Windows so I do not write into the Windows system partition and one LInux format.

WARNING for Windows 8 Dual-Booters
[http://ubuntuforums.org/showthread.php?t=1953674](http://ubuntuforums.org/showthread.php?t=1953674)
It defaults shutdown to a hybrid hibernation/off state for fast boot 
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)
But then files may be corrupted similar to Windows 7 Hibernation:
[http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html](http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html)
[http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot](http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot)

---

### Post by smellyman on 2013-01-20
I am thinking of the xps 8500 as well.  Hope your results are good.

Looking at all those links makes my head hurt.  What a nightmare secure boot is.

---

### Post by unconcrete on 2013-01-20
> **smellyman said:**
> I am thinking of the xps 8500 as well.  Hope your results are good.

Looking at all those links makes my head hurt.  What a nightmare secure boot is.
I agree. If I'd expected such a business, I've bought a new system many months ago.
;)

---

### Post by unconcrete on 2013-01-20
Presume I install Quantal. Probably most of my problems will be solved. 
Actually, I'd use boot-repair to restore grub2, but I haven't enough knowledge to manage the adavanced options. I cannot risk a black screen at reboot, also because I am not the only user of this system. I'll wait February and meanwhile I'll try the links you suggested me.
Two questions: 
.since i need to make use of win8 for commercial software and ubuntu for open source, If i disable secure boot can I dual boot both the OSes or only ubuntu?
.and also, If i choose to try 12.10, it will be possible as soon as possible to install the new Precise LTS and uninstall the 12.10 without MBR damages? 
Thanks in advance.

---

### Post by oldfred on 2013-01-20
The Windows UEFI secure boot specification says the user must be able to turn secure boot off. How the vendor implements that may be a question. Several have posted with their systems, they could boot with secure boot on or off.

I would think whichever Ubuntu you install last will install its copy of grub-efi into /boot/efi/EFI/ubuntu/grubx64.efi and be the one you boot. Then grub.cfg in that install will have chain load entries to other installs like BIOS/MBR does. One user complained & filed a bug as he wanted Ubuntu & Kubuntu to be separate entries in the efi partition like other distributions. But entries were in grub.cfg, so I do not see issue?

I like having multiple installs, but currently only have BIOS, but do have gpt partitioning. I use 25GB for each install but keep all data in separate data partitions so I can use data in every install. With Windows 8 you really need a separate NTFS shared data partition as you never want to do anything with Windows 8 as it is always hibernated (why it boots so quick). Most turn the hibernation off to avoid issues of dual booting.

You may even want two installs of 12.04. It will offer a rolling release type where you have the newest kernel or can keep the old one. But with new hardware you may need the newest kernel to have system work with new hardware.
[https://wiki.ubuntu.com/Kernel/Release/Rolling](https://wiki.ubuntu.com/Kernel/Release/Rolling)

---

### Post by unconcrete on 2013-01-20
I've tried again to install ubuntu and this time it seems successfully. Unnfortunately there is something wrong in the boot loader. In fact only ubuntu starts.
The install process haven't warned me about some error.
At the partition step the default option for grub 2 was /dev/sda and so i've agreed. Actually no boot loader seems to work. 
The only doubt i have is that the grub 2 target is /dev/sda but my uefi partition is /dev/sda1.
Maybe it was better to choose it?
Thanks
unconcrete

---

### Post by oldfred on 2013-01-20
Did you install in BIOS mode or UEFI mode? How you boot install flash drive either UEFI or BIOS is how it installs.

If you install in BIOS mode it uses grub-pc and MBR. If you install in UEFI mode it uses grub-efi and is in efi partition. Boot-Repair can convert from one type to the other.

You cannot chain load from a BIOS install to a UEFI install. Both have to be the same.

Grub still has a bug and does not create correct chain entries to Windows in UEFI mode. But Boot-Repair can fix that.

---

### Post by unconcrete on 2013-01-21
> **oldfred said:**
> Did you install in BIOS mode or UEFI mode? How you boot install flash drive either UEFI or BIOS is how it installs.

If you install in BIOS mode it uses grub-pc and MBR. If you install in UEFI mode it uses grub-efi and is in efi partition. Boot-Repair can convert from one type to the other.

You cannot chain load from a BIOS install to a UEFI install. Both have to be the same.

Grub still has a bug and does not create correct chain entries to Windows in UEFI mode. But Boot-Repair can fix that.

I think my system is uefi, so as i choose usb as the first in boot priority i will have a uefi mode install, but really it is new to me all that. maybe I was making a big mistake. Don-t know.
However I have tried to install boot.repair to solve the prob.
It detect immediately EFI. Then a warning reports ^Warning: this will install necessary packages from Ubuntu-12.10 repositories. Please backup your data before this operation.^ I have installed only 12.04.1 instead. Anyway I go on.
Recommended repair
Create a boot info summary
Advanced options.
In order to avoid options i don t know I choose Recommended.
Follows a series of operations that I think bootrepair try to uninstall grub2 and reinstall it in the correct way.
Finally i have rebooted and after the Dell logo appair the tipical grub menu.
Wow! There are ubuntu uefi mode, windows uefi mode and other i don t remember at the moment. At first i choose Ubuntu and the os works correctly. After that I was satisfied, but at the next reboot I have chosen Windows. 
Black screen of death. The only warning is something like < no bootable disk detected >. 
:&
I remember I ve noticed some warning of boot repair at the end of its process.
<After repair go Bios set Bootpriority:file sda1/efi/ubuntu/shimx64.efi!
The ubuntu boot files are distant from the beginning of the disk.
...
Create partition /boot (ext4 > 200 MB at the beginning of the disk) by using Gparted...select it with the option {Partition / Boot apart}.
At the moment I am confused.
Have I to use the Boot repair advanced options?
What an headache!
I add a snapshot of Gparted. In my hard drive there are for me too much partitions, five of them Dell preinstalled. As boot.repair suggests a new one at the beginning of the disk, where I can create it? it seems a jungle.

unconcrete

---

### Post by oldfred on 2013-01-21
With Windows 8 secure boot your should have 12.10 as it has the newest grub2 2.00. Ubuntu 12.04 has grub2 1.99 but will get the newer version of grub with the next point release in February. Only grub2 2.00 has the secure boot shim that will work with secure boot. If secure boot is off your 12.04 should work.
I do not know if Boot-Repair then installs the grub2 2.00 packages with 12.04 or not. 

If you can boot you do not need the separate /boot at the beginning of the drive. We did see that issue occasionally with BIOS, but I do not think we have seen it yet with UEFI. It as some combination of BIOS, BIOS settings & grub, but by having /boot or the entire / (root) inside the first 100GB would solve that issue. Probably not required for your system.

Boot-Repair will convert a BIOS install to UEFI by uninstalling grub-pc and installing grub-efi. The actual Ubuntu install is the same with just a few setting by grub-efi changed and the efi  version of grub.  

Boot-Repair recognizes you have Windows 8 and suggests booting from UEFI menu with the shim file but with 12.04 you do not have it. With secure boot off you should be able to boot from the ubuntu entry.The shim file has the Windows secure boot key so Ubuntu can work with secure boot.

But you still have to go into UEFI/BIOS and choose ubuntu or else it will just keep booting Windows as the default.

---

### Post by unconcrete on 2013-01-22
At first, I've reinstalled 12.04.1 from my usb as usual. Then I've repeated the boot repair in the same way I did the first time (recommended). I've entered ubuntu and I've upgraded it to 12.10. By the way I hope to install the correct Grub. Upgrade accomplished.
This is the Grub2 menu created by boot-repair:
===================================
Ubuntu
Ubuntu advanced options (?)
Windows UEFI bootmgfw.efi (?)
Windows Boot UEFI Loader (?)
EFI/Dell/Boot/bootmgfw.efi (?)
EFI/Dell/Boot/bootx64.efi (?)
System Setup (?)
===================================
the last time I installed ubuntu the only entries were
UBUNTU
WINDOWS
MEMORY TEST
Of the 7 entries of Grub2 I know only the first one. My goal is always to dualboot the two os. I'd like to know the correct entries to do that.
I've tried to edit  the efi files by doing [sudo gedit ...*.efi] but the file is not text as sources.list or similar files. I don't know what really are these objects and what they do.

Sincerely.
;)

---

### Post by oldfred on 2013-01-22
Boot repair adds two entries to 25_Custom for efi boot. There are two Windows files. bootmgrw.efi and bootx64.efi. These are not editable. 
Grub2's os-prober which runs as part of every sudo update-grub was adding incorrect entries that tried to directly boot to the Windows partitions the way BIOS entires do. But your look from the title as a lot different. Did grub finally fix the bug?

       grub2's os-prober creates wrong style (BIOS) chain boot entry
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383)
Type of entry that does not work:
'Windows ...) (on /dev/sdXY)'

---

### Post by unconcrete on 2013-01-26
> **oldfred said:**
> Boot repair adds two entries to 25_Custom for efi boot. There are two Windows files. bootmgrw.efi and bootx64.efi. These are not editable. 
Grub2's os-prober which runs as part of every sudo update-grub was adding incorrect entries that tried to directly boot to the Windows partitions the way BIOS entires do. But your look from the title as a lot different. Did grub finally fix the bug?

       grub2's os-prober creates wrong style (BIOS) chain boot entry
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383)
Type of entry that does not work:
'Windows ...) (on /dev/sdXY)'

Sorry for the late answer.
I've read the Launchpad article and it is interesting but I am not use to manage with system configuration, since most of the things that the  article reports are actually very difficult to understand. I don't like to create a bigger damage, by trying options I don't know. 
However I've understood the os prober has found wrong information. It is better to fix these info or disable os prober?
Here, I've I've found this hint. [http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=679817](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=679817) Msg. 12.
" My work around was to disable os-prober in grub by adding the line
	GRUB_DISABLE_OS_PROBER=true
at the end of /etc/default/grub then I created a custom entry for windows 7 by adding

	menuentry "Windows 7" --class windows --class os {
        set root='(hd0,gpt3)'
        chainloader (${root})/EFI/Microsoft/Boot/bootmgfw.efi
        }
	
to /etc/grub.d/40_custom and then updating grub by 
	update-grub."

Is it correct in your opinion? And also, I have Windows 8 not 7. 
This can create additional problems?

Regards.

In order to give a better help this is the boot info created by Bot-repair.
[http://paste.ubuntu.com/1572572/]("http://paste.ubuntu.com/1572572/")

---

### Post by oldfred on 2013-01-26
If you look at line 487 Boot-Repair has added a correct Windows boot stanza. Whether set root =  or search are just two different ways to set root. Generally the search to use UUID is preferred as with multiple drives or even plugging in a flash drive may change drive order hd0 becomes hd1 where UUID does not change.

```
### BEGIN /etc/grub.d/25_custom ###

menuentry "Windows UEFI bootmgfw.efi" {
search --fs-uuid --no-floppy --set=root CAF1-3431
chainloader (${root})/EFI/Microsoft/Boot/bootmgfw.efi
}
```

I turn off os-prober. You could turn it back on if grub fixes bug in the future and then you will not need the 25_custom that Boot-Repair has created.
       gksudo gedit /etc/default/grub
GRUB_DISABLE_OS_PROBER=true
or turn off executeable bit
sudo chmod a-x /etc/grub.d/30_os-prober
# then run
sudo update-grub


That will help clean up menu, but will not fix any boot issues.


Perhaps you need this? But I would fully backup entire efi partition first.

       
 Boot-Repair - Updated Jan 1, 2013 to not rename first time, but rename if first time Windows does not boot. Post 706 and 711
[http://ubuntuforums.org/showthread.php?t=1769482&page=71](http://ubuntuforums.org/showthread.php?t=1769482&page=71)
 Boot-Repair copied /EFI/ubuntu/grubx64.efi to /EFI/Boot/bootx64.efi (in case the BIOS is hard-coded to boot into /EFI/Boot/bootx64.efi or secure boot
signed GRUB file shimx64.efi.

   To perform this, just run Boot-Repair --> Adv options --> tick "Backup and rename EFI files" --> Apply
Then reboot the PC and please tell us what you observe.

---

### Post by unconcrete on 2013-01-26
> **oldfred said:**
> If you look at line 487 Boot-Repair has added a correct Windows boot stanza. Whether set root =  or search are just two different ways to set root. Generally the search to use UUID is preferred as with multiple drives or even plugging in a flash drive may change drive order hd0 becomes hd1 where UUID does not change.
...
I turn off os-prober. You could turn it back on if grub fixes bug in the future and then you will not need the 25_custom that Boot-Repair has created.
       gksudo gedit /etc/default/grub
GRUB_DISABLE_OS_PROBER=true
or turn off executeable bit
sudo chmod a-x /etc/grub.d/30_os-prober
# then run
sudo update-grub

That will help clean up menu, but will not fix any boot issues.
Perhaps you need this? But I would fully backup entire efi partition first.
       
 Boot-Repair - Updated Jan 1, 2013 to not rename first time, but rename if first time Windows does not boot. Post 706 and 711
[http://ubuntuforums.org/showthread.php?t=1769482&page=71](http://ubuntuforums.org/showthread.php?t=1769482&page=71)
 Boot-Repair copied /EFI/ubuntu/grubx64.efi to /EFI/Boot/bootx64.efi (in case the BIOS is hard-coded to boot into /EFI/Boot/bootx64.efi or secure boot
signed GRUB file shimx64.efi.

   To perform this, just run Boot-Repair --> Adv options --> tick "Backup and rename EFI files" --> Apply
Then reboot the PC and please tell us what you observe.

I've turned off the os prober, the executable bit and updated grub.
At reboot actually I see the same 7 odd entries:
1) Ubuntu
2) ubuntu advanced options - older kernels
[I]3) Windows UEFI bootmgfw.efi ??
4) Windows Boot UEFI Loader ??
5) EFI/DELL/Boot/bootmgfw.efi ??
6) EFI/DELL/Boot/Bootx64.efi ??[/I]
7) System Setup - dear old Bios
-----------------------------------
You have found a good entry for Windows in my Bootinfo. How can I set it to work as the correct entry in the grub2 menu? Have I to edit particular configuration files or It's better to use Boot -repair?
 If with grub2 the only system to edit the menu is boot repair or other package, I've already saved a backup of my mbr/grub in a usb flash. I need a more detailed info about the advanced options for my case.
In the attach image I show the advanced option untouched. If some option must be grayed and other added, please tell me how to do.
Otherwise, If you think it's better to edit particular config files I need to know their name.
P.S.: my new bootinfo after grub-upfate: [http://paste.debian.net/229026/](http://paste.debian.net/229026/)
Thanks.

---

### Post by oldfred on 2013-01-26
Those are all efi files that Boot-Repair found in your efi folder. They should all boot and also be options to boot from when you are in your UEFI/BIOS menu directly.

If none of them work, then you may have the UEFI/BIOS that only boots Windows and needs the renaming that Boot-Repair can do. Posted above.

---

### Post by unconcrete on 2013-01-27
> **oldfred said:**
> Those are all efi files that Boot-Repair found in your efi folder. They should all boot and also be options to boot from when you are in your UEFI/BIOS menu directly.
If none of them work, then you may have the UEFI/BIOS that only boots Windows and needs the renaming that Boot-Repair can do. Posted above.
Red Alert.
As suggested I have used boot repair to change names. As usual the grub has been uninstalled and reinstalled with the option to rename efi entries.
*The result is a disaster*.
Now no os is avalaible. Only <no bootable device avalaible press a key to retry.> Nothing happens: the monitor is dead. I don t know what happened. Please I need an help. at least I d like to have one of my os working.
The last report of boot repair is the following: [http://paste.ubuntu.com/1576098/]("http://paste.ubuntu.com/1576098/")
Regards.
A note:before the system loss its configuration, as i choose the entry ubuntu as usual, unlike ubuntu starts with its gui, a command line appaired claiming me for user name and password. Without any reason. That happened two times,and after I can reply you only by my usb/flash.

---

### Post by oldfred on 2013-01-27
If you get grub menu and can choose Windows or Ubuntu, and get to login password you have mostly booted, but may have video issues.
Are you then able to get to command line?
You also should be able to boot recovery mode and it may make necessary updates.

What video chip/card do you have?
       How to set NOMODESET and other kernel boot options in grub2 - both liveCD & first boot, but different 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

    
It seems to be having some issues with sdd your 3TB drive with one very large NTFS partition. Several have posted with issues where Windows did not create a valid gpt partition table. 
Download gdisk from repository on live flash drive or install if you can get into it.
       GPT fdisk Tutorial -srs5694 in forums
[http://ubuntuforums.org/showthread.php?t=1439794](http://ubuntuforums.org/showthread.php?t=1439794)
[http://www.rodsbooks.com/gdisk/](http://www.rodsbooks.com/gdisk/)

    
You also have a small SSD as Intel SRT? Some have had issues when the SRT is one and drive still has RAID meta data.
       Intel Smart Response Technology
[http://www.intel.com/p/en_US/support/highlights/chpsts/imsm](http://www.intel.com/p/en_US/support/highlights/chpsts/imsm)
Some general info in post #3
[http://ubuntuforums.org/showthread.php?t=2071242](http://ubuntuforums.org/showthread.php?t=2071242)
Intel SRT - Dell XPS Screen shots of Intel SRT screens
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)
[http://ubuntuforums.org/showthread.php?t=2036204](http://ubuntuforums.org/showthread.php?t=2036204)
Details in post #10 on an install that worked
[http://ubuntuforums.org/showthread.php?t=2020155](http://ubuntuforums.org/showthread.php?t=2020155)
Dell XPS Intel SRT issue on hibernating post #25
[http://ubuntuforums.org/showthread.php?t=1932965](http://ubuntuforums.org/showthread.php?t=1932965)
Some info on re-instating  details in post #9
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)
[http://ubuntuforums.org/showthread.php?t=2070491](http://ubuntuforums.org/showthread.php?t=2070491)
> Disable the RAID, for me it was using the Intel rapid management thingy and telling it to disable the acceleration or the use of the SSD. If you have a different system, just disable the RAID system then install Ubuntu. Once installed you can then re-enable it. 
   > You will need to use the dmraid command prior to running the Ubuntu Installer so that it will be able to see the partitions on the drive because otherwise with the raid metadata in place it will see the drive as part of a raid set and ignore its partitions.

---

### Post by unconcrete on 2013-01-27
No more.
I have no grub menu (wright or wrong) no bootable partitions. Only a black screen.
My video card is nvidia. I'm not working from my home so i haven't the detailed version. I'll give information about as soon as possible. 
Anyway I don't understand what error I've done with boot-repair. I can try to reinstall but I think the problems will be the same.
Sincerely.
this is the reuslt of gdisk:
-------------------------------
sudo gdisk -l /dev/sda
...
Partition table scan:
MBR: protective
BSD: not present
APM: not present
GPT: present

Found valid GPT with protective MBR; using GPT.
Disk /dev/sda: 3907029168 sectors, 1.8 TiB
Logical sector size: 512 bytes
Disk identifier (GUID): 0FF7F015-4185-4E5A-8BBC-98945CDB443E
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 3907024613
Partitions will be aligned on 2048-sector boundaries
Total free space is 1921132477 sectors (916.1 GiB)

Number Start (sector) End (sector) Size Code Name
1 2048 1026047 500.0 MiB EF00 EFI system partition
2 1032192 1114111 40.0 MiB FFFF Basic data partition
3 1114112 1376255 128.0 MiB 0C01 Microsoft reserved part
4 1376256 2400255 500.0 MiB 2700 Basic data partition
5 2400256 1971529727 939.0 GiB 0700 Basic data partition
6 3892652032 3907022598 6.9 GiB 2700 Microsoft recovery part
ubuntu@ubuntu:~$

---

### Post by oldfred on 2013-01-27
gdisk says sda is ok, but BootInfo seemed to have an issue with sdd. Try gdisk on it.

I have an older nVidia and have since they incorporated drivers into kernel needed nomodeset to boot liveCD and on first boot in grub menu. If grub menu does not show, does holding shift key from BIOS/UEFI until menu appears show menu?

If a video issue in grub, Boot-Repair has a gfxmode setting that it will do. Grub tries to use video from install but if that is not working then grub may have issues showing menu.

Default is 640x480 which should work for everyone, or you can change to your exact configuration.
       Boot-Repair --> Advanced options --> GRUB options tab --> tick the "Uncomment GFXMODE" option --> Apply
Boot-Repair --> Advanced options --> GRUB options tab --> tick "Add kernel option: nomodeset" --> Apply

---

### Post by unconcrete on 2013-01-27
My pc is recently bought, I don't think Dell recycles old video cards. Anyway the video card is a Geforce GT640.

I've recovered Win8 by using boot-repair / unchek reinstall Grub / keep active only "restore mbr". Now as expected, it is Ubuntu that is not avalaible. On the basis of my knowledge, it is better for me to avoid other attempts to install grub. I think I've rejoiced as I've seen the rolling Windows progress appair under the Dell logo.
I think I'll wait for ubuntu precise pangolin LTD 12.04.2 last news say coming on February. Bios/uefi, bootloader are not toys. Or better, they are not toys for me.
Bye.

---

