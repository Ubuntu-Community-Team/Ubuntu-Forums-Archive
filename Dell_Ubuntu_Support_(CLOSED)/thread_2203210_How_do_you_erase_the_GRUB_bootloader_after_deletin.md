---
title: "How do you erase the GRUB bootloader after deleting Ubuntu partitions? Inspiron 3521"
date: 2014-02-02
forum: Dell Ubuntu Support (CLOSED)
---

### Post by danny.techify on 2014-02-02
I dual booted Ubuntu and Windows 8 and now I just wanted Windows 8. So I erased the partitions and all that stuff but when I restarted when I went to a grub screen that talked about some stuff and then on the bottom it had grub>. So I used a recovery USB drive and I went to troubleshooting and to the command prompt and I did the fixboot and fixmbr command but it didn't work, it went to that grub screen again. So to boot into Windows I went to my boot menu and I noticed that there was a option for Ubuntu which didn't make sense to me since I erased the Ubuntu partitions and it appeared twice. Once it said "Ubuntu" and there was another option that said "ubuntu" lowercase:confused: I clicked on Windows Boot Manager which means Windows 8. I can boot into Windows 8 fine without problems.

So can someone tell me how I can make it go straight to Windows 8?

---

### Post by danny.techify on 2014-02-02
[IMG]http://members.iinet.net.au/~herman546/p15/fig2grub.gif[/IMG]
This is the screen I get

---

### Post by oldfred on 2014-02-02
Is this pre-installed Windows 8 with UEFI and gpt partitions?

If UEFI you also have to delete the Ubuntu folder in the efi partition and then manually delete the ubuntu entries in the UEFI. UEFI saves boot entries in its own NVRAM and Windows 8 syncs those into its BCD.

If you do not delete the Ubuntu folder in efi partition, UEFI will just readd the entries.

       Really UEFI boot menu 
[http://askubuntu.com/questions/63610/how-do-i-remove-ubuntu-in-the-bios-boot-menu](http://askubuntu.com/questions/63610/how-do-i-remove-ubuntu-in-the-bios-boot-menu)
[http://linux.die.net/man/8/efibootmgr](http://linux.die.net/man/8/efibootmgr)
# from live CD and use efibootmgr
sudo efibootmgr -v
The "-v" option displays all the entries so you can confirm you're deleting the right one, and then you use the combination of "-b ####" (to specify the entry) and "-B" (to delete it). Examples #5 is delete:
[http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD](http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD)
[http://software.intel.com/en-us/articles/efi-shells-and-scripting/](http://software.intel.com/en-us/articles/efi-shells-and-scripting/)
Launch EFI Shell from File System Device
[https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface#UEFI_Shell](https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface#UEFI_Shell)

---

### Post by danny.techify on 2014-02-02
It has UEFI and it has Windows 8.1 but I don't know what gpt partitions are. How do I know which partition is the UEFI?

---

### Post by danny.techify on 2014-02-02
How do I access the UEFI partition. It don't see anything like that in This PC.

---

### Post by danny.techify on 2014-02-02
Also why is Ubuntu showing twice in my boot menu?

---

### Post by oldfred on 2014-02-02
It probably is showing both grub & shim or the secure boot version of grub that has the Microsoft signing key. Both are in the ubuntu folder in the efi partition.

You have to use Live installer. Which will show the efi partition. It is FAT32 with the boot flag.

There are procedures from Windows, but do not know details. You have to use command line and manually mount the FAT32 partition so it becomes a drive. Normally Windows will not show the efi partition.

A few better UEFI will let you do all of it from the UEFI menu.

---

### Post by danny.techify on 2014-02-08
So once I get into the UEFI partition I can just delete the Ubuntu folder?

---

### Post by oldfred on 2014-02-08
Its the efi partition from Linux, also known as ESP.
Delete Ubuntu folder, but not Windows nor boot.

You should see these in the FAT32 formatted partition:
 /EFI/Boot
/EFI/Microsoft
/EFI/ubuntu

---

### Post by danny.techify on 2014-02-08
So I get my Ubuntu live disc and I go into the file explorer and I find the Uefi partition and delete the Ubuntu folder.

How do I actually get into the partition on Ubuntu using the live CD? Do I need program or anything or what?

---

### Post by oldfred on 2014-02-08
The file explorer is also called Nautilus. It should just let you delete that.

If unsure what partition is what you can run this from terminal.
sudo parted -l

The FAT32 partition is the efi partition.

It may look something like this except you have Windows partitions.

```
Number  Start   End     Size    File system  Name        Flags
 1      20.5kB  500MB   500MB   [COLOR=#ff0000]fat32 [/COLOR]       [COLOR=#ff0000]EFI System[/COLOR]  boot
 2      500MB   501MB   1049kB                           bios_grub
 3      501MB   15.2GB  14.7GB  ext4         sys

```

---

### Post by danny.techify on 2014-02-08
Can you please explain step by step since I don't know much about the terminal.

---

### Post by oldfred on 2014-02-08
You should not need terminal. But from Nautilus not exactly sure how it will show efi partition in left panel. It may say efi or just 300MB partition, or something else?

---

### Post by danny.techify on 2014-02-08
So if it does not show in Nautilus how do I erase the folder through terminal ? Can you explain step by step?

---

### Post by oldfred on 2014-02-09
To open terminal
ctrl-alt-T

Then in terminal list partitions
sudo parted -l

Find partition that is FAT32 formatted, I will use sda1, but if sda2 or sda3 change all sda1 to sda2 etc.
       sudo mkdir /media/efidata
      
 sudo mount /dev/sda1 /media/efidata

Now in nautilus it should show as efidata in left panel
gksudo nautilus

---

### Post by danny.techify on 2014-02-09
[FONT=arial]OK I am in the live installer and I went into nautilus and I found something on the left side that said "367 MB Volume", when I click it it gives me an error that says
[/FONT][B]
Error mounting /dev/sda6 at /media/ubuntu/0046C1A246C198B4: Command-line `mount -t "ntfs" -o "uhelper=udisks2,nodev,nosuid,uid=999,gid=999,dmask=0077,fmask=0177" "/dev/sda6" "/media/ubuntu/0046C1A246C198B4"' exited with non-zero exit status 14: The disk contains an unclean file system (0, 0).
Metadata kept in Windows cache, refused to mount.
Failed to mount '/dev/sda6': Operation not permitted
The NTFS partition is in an unsafe state. Please resume and shutdown
Windows fully (no hibernation or fast restarting), or mount the volume
read-only with the 'ro' mount option.
[/B]

---

### Post by oldfred on 2014-02-09
That is probably is not your FAT32 efi partition. It normally is one of the first three partitions.

 Did you leave Windows hibernated or have other NTFS partitions on drive?
Or it may need chkdsk which you have to run from Windows or your Windows repairCD or flash drive.

---

### Post by danny.techify on 2014-02-22
[SIZE=3][FONT=century gothic]I found a way to get into the EFI partition with the Windows command prompt and I mounted the partition and I deleted the ubuntu folder.

Thanks![/FONT][/SIZE]

---

