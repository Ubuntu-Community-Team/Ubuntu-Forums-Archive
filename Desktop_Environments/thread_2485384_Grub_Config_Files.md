---
title: "Grub Config Files"
date: 2023-03-28
forum: Desktop Environments
---

### Post by Geoff_Lane on 2023-03-28
I have a multi boots system, Ubuntu-Server running iceWM, Linux MX running KDE and Arch runnng xfce.  Also installed is Windows but cannot recall the last time I booted in to that.

I am aware all the Linux systems have grub config files in /boot/grub  /etc/grub.d and /etc/default  -  I am also aware that the ESP partition is pointed to /boot/efi

What confuses me is which system's /etc/grub.d and /etc/default files are used?

Geoff

---

### Post by oldfred on 2023-03-28
You have to manage which install's grub is the default in the ESP.
If a system does a major upgrade or you install another system, it typically overwrites /EFI/ubuntu/ with that install. If your default is another install, you need to boot back into it and reinstall grub from there.

Only the UUID in the ESP determines which system will be booted. Reinstall of grub updates that & entry in UEFI.  I have also edited the UUID to change default in ESP when new install has overwritten it. Entry in UEFI for all Ubuntu official and many unofficial flavors is Ubuntu. I think Debian uses grub and other distributions use their name.

I change distributor in grub, so I get different folder in ESP like jammy, but it has not worked in past as it always used ubuntu folder for grub.cfg, even though my jammy folder has a grub.cfg.
From this where Boot000 is default, I have many others.
> sudo efibootmgr -v 
[FONT=monospace][COLOR=#000000]Boot0001* jammy HD(1,GPT,c90a60b4-dbf4-4ab4-af2c-e2c7c03eeed1,0x800,0x100000)/File(\EFI\JAMMY\SHIMX64.EFI)[/COLOR]


[/FONT]

This is my /boot/efi/EFI/ubuntu/grub.cfg in the ESP.
```
search.fs_uuid 9da6b198-e2ca-4e27-8a18-6daf4ecfc324 root 
set prefix=($root)'/boot/grub'
configfile $prefix/grub.cfg
```

UEFI uses partUUID/GUID to find ESP to use for booting. 
Grub.cfg in ESP uses UUID to find install.
You can see UUIDs & partUUIDs.
```
lsblk -e 7 -o name,fstype,size,fsused,label,partlabel,mountpoint,uuid,partuuid
```

---

### Post by Geoff_Lane on 2023-03-29
I currently have a very odd scenario whereby my GRUB menu has disappeared and my device boots to my Arch Linux system.  I had previously done a grub-install to attempt to remedy a booting issue but since then the menu has disappeared.   This suggests I have messed up the boot sector so I connected an external device that had three Linux OSs installed and has worked fine using its own GRUB menu, cannot get that one to show either, computer, after delay goes to internal HD and boots Arch.

Had two external USB memory keys that had tails installed, one didn't work but fortunately one displayed a GRUB menu so I was able to manually boot my Ubuntu-Server and my MX-Linux system.  Tried grub-install then update-grub - no errors reported but still no GRUB menu.

For time being using supergrub rescue disk.

This may be coincidental but one observation, of my two USB memory keys that have tails installed the USB3 fails to display a menu, the USB2 device displays a GRUB menu.  My external device with three systems installed is also USB3 and does NOT display a GRUB menu, my supergrub image is loaded onto an old USB2 memory key, that works. -

Currently my laptop is set to boot to USB then internal SSD - I have tried altering the order and manually selecting the USB device but this makes no difference.

Geoff

---

### Post by oldfred on 2023-03-29
Did you update UEFI? Or change settings to defaults in UEFI?
That will reset UEFI to default settings & you have to redo all the settings you changed to get Ubuntu/Linux to work.

To see all the details on your configuration you can run the Boot-Repair Summary Report. It does require a GUI, so I do not think it works with server, typically need desktop live installer.

Please copy & paste the pastebin link to the BootInfo summary report ( do not post report), do not run the auto fix till reviewed. Use often updated ppa version over somewhat older ISO with your USB installer  or any working install.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) & 
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by Geoff_Lane on 2023-03-30
I have a lightweight Windows Manager on my server (IceWM) so running it no problem.

I did not knowingly update UEFI

Here is the pastebin link prior to trying the boot-repair repair options;

[https://paste.ubuntu.com/p/42CCgNxptk/](https://paste.ubuntu.com/p/42CCgNxptk/)

Geoff

---

### Post by oldfred on 2023-03-30
Boot-Repair says you have legacy Windows, but that cannot be correct since on gpt drive.
But it probably says that as it sees NTFS Windows partition, but no UEFI boot entry for Windows.
Windows requires gpt partitioning for UEFI boot. And if gpt it can only be UEFI boot.

Ubuntu will let you boot in BIOS mode from gpt or UEFI boot mode from MBR(msdos).
But you should only use UEFI/gpt if system is UEFI hardware and especially if you have Windows in UEFI boot mode.

You have a BIOS grub install to MBR of sda on gpt drive.  It says it is booting sda5, Debian, but grub with gpt needs a bios_grub partition. But better to have install in sda5 as UEFI boot. Only difference with UEFI and BIOS installs is the version of grub, grub-pc for BIOS and grub-efi-amd64 for UEFI boot with 64 bit PCs. Not sure if Debian would boot if you change system to BIOS/CSM/Legacy boot and boot thru MBR even though missing bios_grub partition. 

You also have no UEFI boot entry for Windows. That would require a Windows repair/recovery flash drive booted in UEFI mode & running the standard set of Windows repairs. 

It looks like issue is or was that Debian was installed in BIOS mode or converted to BIOS boot with incorrect version of grub. 
Not sure what happened to Windows boot files. ESP (sda1) may have been reformatted during one of the UEFI installs, erasing Windows boot files/folder. All installs should share same ESP.
How you boot install media, UEFI or BIOS is then how it installs or makes repairs. So always boot in UEFI mode.

Not sure where it found the install on sdb?

---

### Post by Geoff_Lane on 2023-03-31
Debian is on an external USB drive that was not connected when I ran the boot-repair program for this data. The external drive  I use for practice, had it for ages and also had numerous different OSs on there. Debian is not on my main internal drive which is an SSD and was cloned over from a previous mechanical HD,  Has its own GRUB menu.  

When I ran the program to create the log the only OSs that would have been available would have been Ubuntu-server, Linux MX and Arch along with Windows.

All has been working fine for months, had absolutely no issues other than occasional hiccup when I use the external drive to boot an OS as updates used to affect my GRUB menu.  As for Windows, that was left over from the purchase of the computer, I shrunk the partition down ages ago, not sure why I keep it really.

I shall try the Ubuntu Boot-Repair but currently am using SuperGrub Rescue on a USB memory key which fortunately shows me all my options.

Geoff

---

### Post by oldfred on 2023-03-31
With multiple installs, you have to manage grub.
Each install with updates may reinstall grub & make that install first in boot order whether UEFI or BIOS.
But you should always be able to boot into main working install from grub menu or UEFI.
But if installs use same name/label like Ubuntu or grub then only one install will boot. 

With external drives you should always select to install grub to external drive, so it can be booted without internal drive. 
There is a bug with UEFI, so you have to manually create an ESP - efi system partition as FAT32 with boot,esp flags. And do one of several work arounds to get grub to install to the external drive. I think Debian worked ok, but Ubuntu only installs grub to internal drive, no matter what you select during install.
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379)

I would use Boot-Repair's advanced mode & choose install & choose drive to install grub.
Advanced mode screens.
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by Geoff_Lane on 2023-03-31
Thanks Fred,

I think my main issue may have been when I switched to an SSD from mechanical I used Macrium Reflect for Windows back up, so this was the original boot.  Used an external linux image to shrink the partitions then installed my Linux systems.

A recent accidental  installation wiped the disk, I was able to recover most of the data using Linux recovery tools, think from memory I actually used gparted to copy Arch from my external drive to my SSD, amazingly it worked.

On reflection guess it is amazing it all worked without issue, I am wondering now how to get back to some GRUB menu but for now SuperGrub rescue is doing it fine, just not so pretty :cool:

Geoff

---

### Post by yancek on 2023-04-01
> I am wondering now how to get back to some GRUB menu but for now SuperGrub rescue is doing it fine, just not so pretty 

Generally what happens is the last OS installed will be the one with the Grub (or BCD with windows) menu.  Windows won't show Linux entries on a default install.  If you want to boot windows from Grub, windows must be installed in the same mode as Grub (EFI or Legacy).  This is explained in posts 6 and 8 by oldfred.

Your boot repair output shows EFI files for MX and Arch but not for Ubuntu or Debian although all four appear on the first drive (sda).  You should be able to boot all 4 from Grub either Legacy or UEFI but not windows.  I would be surprised if you could boot windows as it is on a GPT drive but has no UEFI files.  Boot into the Linux OS you want to handle the bootloader and install Grub to the MR (if Debain or Ubuntu) and to the EFI partition if it is MX or Arch.  After this from that same OS, update Grub and you should have a menuentry for all 4 Linux OS's but NOT windows.

---

