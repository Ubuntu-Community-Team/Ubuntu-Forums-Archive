---
title: "Is Ubuntu interfering with Windows setup?"
date: 2014-08-19
forum: Desktop Environments
---

### Post by axelsword on 2014-08-19
Hi!

I've run into a Windows setup problem. I'd like to know if Ubuntu is interfering with the setup process before I wipe the HDD.

Recently my Windows 7 broke down and won't start. It came with the laptop when I purchased it. I added an SSD HDD later to speed up overall computer experience. I installed Ubuntu 12.04 LTS on the SSD first.
Here's the current HDD setup as shown by disk utility:

/media/OS is where the Win7 is installed to.
The SSD:

the highlighted partition is where I intended to install Windows 8.1

During the Windows setup I get this error:
I
*Edit* I already tried using "Delete" from windows setup on that 27gb partition and then "New", but still no luck. I'm more concerned about the way Ubuntu overwrote Win7 boot screen information.
I'm left buffled. Windows won't install even over the Win7. I get this same error for every partition listed (see image links below).
Any tips you can offer? I'd like to have both os on the faster SSD drive, but I'm reluctant to experiment, since I don't want to wipe Ubuntu and be left without a working computer.

Some additional images:
[current boot screen]("http://imgur.com/qD0yF8x.jpg")
[BIOS boot setup]("http://imgur.com/zw3kADF.jpg")
[windows 8.1 setup screen 1]("http://imgur.com/Z94mbrB.jpg")
[windows 8.1 setup screen 2]("http://imgur.com/sYj6Bfs.jpg")
[windows 8.1 setup screen 3]("http://imgur.com/5RDEaCG.jpg")
[windows 8.1 setup screen 4]("http://imgur.com/eRvNcO2.jpg")
[windows 8.1 setup screen 5]("http://imgur.com/NqcyV05.jpg")
[windows 8.1 setup screen 6]("http://imgur.com/qjSORPz.jpg") (to open console press Shift+F10)
*Edit* I need current DirectX to play StarCraft 2 Heart of the Swarm. No other attachments to Windows.

---

### Post by yancek on 2014-08-19
Have you tried using your windows 7 Recovery disk to set the windows drive back to factory default?  If so, what happens?
The error message you posted indicating that windows 8 could not be installed as the drive contains a GPT partitioning scheme is a bit weird.  Windows 8 can certainly be installed to a GPT drive.  Do you have an option to select GPT/UEFI during your installation?  I'm not familiar with windows 8 so don't have any suggestions but I'm sure someone else will.

You should have a FAT32 partition for the UEFI files somewhere, probably on the 1TB with windows 7.  You could try googling 'bootinfoscript' and downloading and running it from Ubuntu as it will show more information which could lead someone to pointing out a solution.

---

### Post by grahammechanical on 2014-08-19
May I suggest something? You use the Windows 8 install disk to format that 25GB partition on the SSD and then run the Windows 8 installer.

The other year when I tried to install a Windows 8 preview edition it refuse to install. First, I had to format the partition  then when I ran the installer it accepted my directions on which partition to install into.

A partition without a file system (format) might be the reason that the Disks utility is showing it as "unknown."

Regards.

---

### Post by willbe1kenobi on 2014-08-19
I also had a similar issue a few weeks back and I remember that the drive that I had installed Win 8 had to be formatted first before it could be installed. Make sure you back up the important data on the other partitions first.

---

### Post by axelsword on 2014-08-20
I tried those commands at the partition selection screen to format, create new and delete partition. Could be just the hidden partitions the setup wants to create. I'm not sure, but I'll have to go the hard route and wipe Ubuntu, then hopefully re-do all the setup, conf files and other modifications.

---

### Post by axelsword on 2014-08-22
Well, I'm still fidling with Windows 8.1 and Ubuntu 14.04 LTS
This came up

[Link to original image size and quality]("http://i.imgur.com/Lbitmpd.png")

The installer didn't detect any partitions, but luckily live cd sees them all right.
Will update on how it goes

---

### Post by oldfred on 2014-08-22
It sounds like you had a MBR/BIOS install of Windows 7.
Then in installing Ubuntu converted drive to gpt.

Windows only boots from gpt partitioned drives with UEFI.
Both Windows & Ubuntu only boot from MBR(msdos) drives with BIOS.

Typical Windows 7 installer defaults to BIOS install. You have to convert to flash drive and run some updates to convert to UEFI installer.

How you boot installer from UEFI/BIOS is how it installs, for both Windows & Ubuntu.
So if you boot install media in UEFI mode it will install in UEFI boot mode.
But if drive is gpt and you boot Windows in BIOS Mode it will complain as you have seen. Drive must be MBR to install in BIOS mode.

---

### Post by axelsword on 2014-08-22
Thanks for your answers.

User oldfred[**[COLOR=#C61919][B]**[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=852711"), could you give a link to some more resources on the topic or explain more?
Right now I've deleted everything. I've installed Windows 8.1 three times now and the direct problem now is that Ubuntu 14.04 LTS setup doesn't recognize partitions nor the installed windows.
When I boot ubuntu from live cd, then I can see the windows partition and files all right. Installing ubuntu is a no go, since at the partition select screen it shows the hdd as blank without any partitions.

All I did with Ubuntu is download the iso image as always, burn to blank RW dvd disk and restart the pc.
If Ubuntu is already installed, then Windows doesn't offer to setup double boot.

Right now I can't install Ubuntu, because it "erases" windows, as if it was never installed.

---

### Post by oldfred on 2014-08-22
Ubuntu has a major bug but they say that is how it is supposed to work???
       Reinstall says overwrite Ubuntu but it also erases existing Windows.
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192)

Did you install Windows in UEFI or BIOS boot mode. You want Ubuntu in the same boot mode and both install in the same mode as you boot installer. 
UEFI and BIOS/CSM/Legacy are not really compatible and booting one system in one mode and one in the other mode is possible if Windows is UEFI as Ubuntu can boot in BIOS or UEFI from a gpt partitioned drive.
But if drive is MBR(msdos) for BIOS boot then you can only install both systems in BIOS mode.

You should have settings in UEFI/BIOS, such as UEFI with secure boot on or off and when secure boot is off, then you should have a CSM boot option.
      
 CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode 
Some only have secure boot on or off and then boot in first mode found UEFI's efi partition  or BIOS MBR on hard drive. But you should get two options on flash drive or DVD.

If drive is gpt partitioned and Windows is booting in UEFI mode. Make sure fast boot is off as that is always on hibernation. And usually better to have secure boot off, although Ubuntu will work with secure boot on, but grub will not currently boot Windows 8.1 from its menu if secure boot is on (bug), you have to use UEFI or one time boot key to choose Windows or Ubuntu then.

      
 Shows install with screen shots for both BIOS(purple) & UEFI(grub menu), so you know which you are using.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Also shows Windows 8 screens
[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system)
[http://askubuntu.com/questions/163962/install-alongside-option-missing-how-do-i-install-ubuntu-beside-windows-using](http://askubuntu.com/questions/163962/install-alongside-option-missing-how-do-i-install-ubuntu-beside-windows-using)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot. required for UEFI & grub bug fixes
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
[http://www.rodsbooks.com/linux-uefi/](http://www.rodsbooks.com/linux-uefi/)

    
Use Windows own partition tools to shrink Windows and make unallocated space, reboot immediately to let it run chkdsk and update to its new size. Make sure fast boot is off as it likes to turn it on.
If an Ultrabook or dual video see additional info in link in my signature.


 Any install with Something Else which is required with  external drives or any second drive or any install with separate /home
Also shows combo box with location of grub2 boot loader
[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)
Does not hightlight changing boot loader to sdb, if external drive, but shows other install screenshots:
[http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot](http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot)
[http://askubuntu.com/questions/274371/install-on-second-hard-drive-with-startup-boot-optiond](http://askubuntu.com/questions/274371/install-on-second-hard-drive-with-startup-boot-optiond)
Install 14.04 Something Else explanation and screenshots (note boot load to VM, most may install to MBR of drive sda, or sdb)
[http://www.tecmint.com/ubuntu-14-04-installation-guide/](http://www.tecmint.com/ubuntu-14-04-installation-guide/)

Post this from Ubuntu live installer, if you have working Windows on drive.

sudo parted -l

---

### Post by axelsword on 2014-09-03
The guides don't make sense to me.

1) I turned off fast start-up in power options
2) this is what the powershell reports
[IMG]http://i.imgur.com/EAsUYhY.png[/IMG]
So as far as I understand I don't have secure boot support.
The only thing with UEFI is in BIOS, I've got this screen-shot in OP. Once more, here
[http://imgur.com/zw3kADF.jpg](http://imgur.com/zw3kADF.jpg)
I don't know how to check which mode Windows 8.1 is installed in. All I know is that Ubuntu setup does not display the partitions where Windows sits. When I select "something else", it just shows one green line, even though I can open the partitions in Nautilus and browse the files.
I'll make a screen-shot of Ubuntu setup sometime.

Note: The only way to install Windows 8.1 was to delete everything. I have two HDD's in the computer, but setup wouldn't proceed until both disks were clean. The setup didn't give an option in which mode to install Windows (either MDR or UEFI).

---

### Post by yancek on 2014-09-03
Reading through these posts again, the post by OldFred above indicates that you had originally had windows 7 on the computer and it was installed in MBR mode, not using UEFI and GPT partitioning.  You apparently then installed Ubuntu in UEFI mode with GPT partitioning as seen in one of the images you posted earlier.  My understanding is that they all need to be MBR or they all need to be UEFI which was not the case in your situation.  

You may not have Secure Boot as it is just an add-on to UEFI for microsoft windows systems to try to boot them more securely.
The Ubuntu installation medium should have an option to install in UEFI, since I don't use UEFI you'll need to wait for someone else to respond.
Some info from the microsoft site:

[http://technet.microsoft.com/en-us/library/hh824987.aspx](http://technet.microsoft.com/en-us/library/hh824987.aspx)

---

### Post by axelsword on 2014-09-11
I'll summarize and make it simple

The image will tell the issue I'd like to solve:

[ATTACH=CONFIG]256379[/ATTACH]

[Link to proper image quality]("http://i.imgur.com/VM3swNF.png")

Situation before getting to Ubuntu installation:
[LIST=1]
[*]Installed Windows 8.1 while wiping all partitions on both HDD's 
[*]In BIOS boot setup selected "boot from DVD drive (uefi)" 
[/LIST]

Conclusion: setting up dual boot fails.

As seen from the install window, Ubuntu setup does not detect any partitions on the 250 gb disk, where Windows is installed. I've tried. Even if I don't touch that disk, after Ubuntu installation there's no way to boot to Windows.

Strangely there's two BIOS entries to boot from CD, one is prefixed with "UEFI". To make the screen-shot, I used that mode. It seems that didn't force Ubuntu live CD in uefi mode.

So, I'd really appreciate clear step by step. Don't just give me links to resources, because I didn't find the part that explains how to boot or install Ubuntu in uefi mode. Or maybe just force Windows into MBT mode.

Thanks!

P.S.
I refuse to experiment any further with installing Windows, then Ubuntu, then Windows again, because to play Starcraft 2, it first downloads 13gb update, which takes about hour and a half.

---

### Post by oldfred on 2014-09-11
It seems to be normal for Ubuntu not to see Windows 8 with UEFI. But if you partition in advance and use Something else it will install correctly.
But if you installed Windows in BIOS/MBR mode and drive was gpt, Windows does not correctly convert from gpt to MBR and that must be fixed first.

Please do not post screen shots in line. You can use advanced mode and paperclip icon to attach screen shots. 
Also with terminal output please just copy it from terminal to post. And if longer use code tags to make it easier to review. In advanced mode you can easily add code tags with the # icon.

We have to know if you installed Windows in BIOS or UEFI boot mode.
Post this from terminal in Ubuntu live installer.

sudo parted -l
sudo fdisk -lu

If drive is gpt partitioned the fdisk may show caution on gpt drive and just show one gpt partition which is correct as fdisk does not work on gpt drives.

---

### Post by axelsword on 2014-09-24
Ok, here is the full glory!

I ran both commands. Here's the result

```
ubuntu@ubuntu:~$ [COLOR=#ee82ee]sudo parted -l[/COLOR]
Model: ATA ST1000LM024 HN-M (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt

Number  Start   End     Size    File system  Name                  Flags
 1      1049kB  35.0GB  35.0GB  ntfs         Basic data partition  msftdata
 2      35.8GB  35.8GB  35.7MB  fat32                              boot
 3      35.8GB  1000GB  964GB   ntfs         Basic data partition  msftdata


Warning: /dev/sdb contains GPT signatures, indicating that it has a GPT table.
However, it does not have a valid fake msdos partition table, as it should.
Perhaps it was corrupted -- possibly by a program that doesn't understand GPT
partition tables.  Or perhaps you deleted the GPT table, and are now using an
msdos partition table.  Is this a GPT partition table?
[COLOR=#ff8c00]Yes/No? y [/COLOR]                                                                
Model: ATA Samsung SSD 840 (scsi)
Disk /dev/sdb: 256GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start  End  Size  File system  Name  Flags


Model: MATSHITA BD-MLT UJ240AFW (scsi)
Disk /dev/sr0: 4700MB
Sector size (logical/physical): 2048B/2048B
Partition Table: mac

Number  Start   End     Size    File system  Name   Flags
 1      8192B   24.6kB  16.4kB               Apple
 2      3979MB  3989MB  9568kB               EFI


ubuntu@ubuntu:~$ [COLOR=#008000]sudo fdisk -lu[/COLOR]

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0xb7b9d1ee

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1  1953525167   976762583+  ee  GPT
Partition 1 does not start on physical sector boundary.

WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdb: 256.1 GB, 256060514304 bytes
255 heads, 63 sectors/track, 31130 cylinders, total 500118192 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xb7b9d1ea

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048    71935999    35966976    7  HPFS/NTFS/exFAT
/dev/sdb2        71936000   500113407   214088704    7  HPFS/NTFS/exFAT


```

---

### Post by oldfred on 2014-09-24
Your 1TB drive is gpt and it looks like your 256GB drive is now MBR, but was gpt. If that is a Windows install, Windows installed in BIOS mode converts a gpt drive to MBR, but does it incorrectly. It leaves the backup gpt partition table, so then Linux tools see both MBR & gpt and assume you want to totally start over.

Better to have both drives as gpt if booting in UEFI mode. 
If you have Windows in BIOS mode then better to have Ubuntu in BIOS boot mode, but Ubuntu only drive can be gpt partitioned.
Windows only boots from a gpt drive with UEFI.
Ubuntu boots from gpt with UEFI or BIOS if you have correct partitions.
Windows & Ubuntu only boot from MBR(msdos) partitioned drives with BIOS. 

Windows 7 can be installed in UEFI boot mode with gpt, but you usually have to convert DVD to flash drive and run some updates.
If BIOS is both UEFI & BIOS, how you boot install media UEFI or BIOS will be how it installs.

If you want to keep Windows in BIOS mode, then you should run fixparts to remove backup gpt partition from the Windows drive.
       FixParts is the easiest way to remove the stray GPT data. GPT fdisk (gdisk or sgdisk) can do it, but the procedure's a bit more involved.
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)


 GPT Advantages (older but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
UEFI Advantages
[http://askubuntu.com/questions/446968/legacy-vs-uefi-help](http://askubuntu.com/questions/446968/legacy-vs-uefi-help)

---

### Post by axelsword on 2014-09-26
Ok, listen. Thanks for the help.

Is it possible to set up Ubuntu along side Windows 8.1 ? The last time I tried creating bootable Windows 7 USB, I ran into that one error which was an exception. Can't remember what the deal is.

I've purchased Win8 install. It came in a DVD. That's it. That's all I got. I just downloaded Ubuntu iso and burned to re-writable DVD.

So, can it be done? Will this f-disk wipe the hidden GTP partition or whatever?

Thanks.

---

### Post by oldfred on 2014-09-26
I believe it is the same with Windows. How you boot installer whether DVD or flash drive is how it installs. I have seen where with Windows 7, you have to copy DVD to flash drive and do a couple of updates to make it UEFI capable. 

But Windows 8 has its own issues. You must make sure fast boot or always on hibernation is off. And if hardware has secure boot usually better to have that off.

Which ever drive you install Windows into make sure that is the default boot for the system. Windows will install its boot loader to the BIOS default boot even if not same drive as you are installing. 
Ubuntu installs its boot loader to sda by default even if that is not the drive you install into, but using Something Else or manual install you can specify which drive.
If unsure, often best to just disconnect one drive so system can only install to that drive.

Windows only boots from a gpt drive with UEFI.
Windows on boots from a MBR drive with BIOS.
And how you boot installer is how it will install.
Always best to have both Ubuntu & Windows in same boot mode either both UEFI or both gpt.
But Ubuntu can boot from a gpt partitioned drive with BIOS or UEFI if you have correct supporting partitions. There are even ways to get Ubuntu to boot either way on same drive.
Windows will also read data partitions on a gpt drive if formatted to NTFS even if in BIOS mode on a MBR partitioned drive.

---

