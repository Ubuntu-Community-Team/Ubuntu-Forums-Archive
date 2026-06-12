---
title: "seagate driver"
date: 2009-03-25
forum: General Help
---

### Post by samster500 on 2009-03-25
am new to Ubuntu and having trouble viewing files on my usb seagate external drive i.e. no access to them.

this is Ubuntu's last chance - I haven't the time to look for and download drivers for all my hardware.  Is there a quick and painless solution (I know..go back to using Windows).

---

### Post by coffeecat on 2009-03-25
> **samster500 said:**
> this is Ubuntu's last chance - I haven't the time to look for and download drivers for all my hardware.

The driver for USB external drives is already compiled into the kernel. You don't need to download anything. That's a Windows wasy of thinking.

There's probably something in the way in which your Seagate drive is formatted which is preventing Ubuntu from accessing it. Or some manufacturers put special Windows software on the drive that interferes with any non-Windows OS from reading it.

Is the drive working OK in Windows? What happens when you plug it into Ubuntu and switch it on? Does a window appear on the desktop? Or an error message? Or nothing at all?

If nothing at all, open a terminal, and run the following command:

```
sudo fdisk -l
```You'll be prompted for your password. Type it in but it won't be echoed to the screen. Post the output. (By the way, that's a lower-case L, not a 1/one.)

---

### Post by samster500 on 2009-03-25
the hard disk is working fine in windows; but nothing appears 
on the desktop when I plug it into my other laptop running Ubuntu.

this is the output from  fdisk -l

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x85db54c2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       11977    96205221   83  Linux
/dev/sda2           11978       12161     1477980    5  Extended
/dev/sda5           11978       12161     1477948+  82  Linux swap / Solaris

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x170a8ae2

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       38913   312568641    c  W95 FAT32 (LBA)

---

### Post by 3Miro on 2009-03-25
> 

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x170a8ae2

Device Boot Start End Blocks Id System
/dev/sdb1 * 1 38913 312568641 c W95 FAT32 (LBA) 



Unless you have two hard-drives in your computer, this is the external Seagate. Note that it is formated for win95 using the outdated Fat32 format. I am not sure why it doesn't auto-mount (Ubuntu reads fat32), but I guess you can try to manually mount the device. If you go to Places -> Home, look on the left side of the window, do you see things like Desktop, File System, Network, CD/DVD ... somewhere in the you should see the external hard listed (I am not sure what it would be listed as), click on it should open.

Post if it doesn't.

---

### Post by coffeecat on 2009-03-25
This is the important bit:

> **samster500 said:**
> Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x170a8ae2

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       38913   312568641    c  W95 FAT32 (LBA)

It identifies your external drive as 320GB, and formatted FAT32. There's absolutely no reason why Ubuntu shouldn't mount that drive and let you access it. Linux has had Fat32 read-write capabilities since - oh - about the age of the dinosaurs.

Some things to check:

1 Did the Seagate drive come with any software of any description? Encrypting, archiving, anything? Or have you been saving encrypted files from Windows?

2 In Ubuntu, plug the drive in and swicth on. Now (in the main menu - top left) go to Places > Removable Media. Is it there? It's just possible the drive is being mounted but that an icon is not popping up on the desktop for some reason.

If that doesn't help, go to Places > Home Folder and click. A nautilus window will open up with your home folder. In the Nautilus menu, go to Edit > Preferences and then the 'Media' tab. Is the 'Browse media when inserted' box ticked? If not, tick it.

---

### Post by samster500 on 2009-03-25
Have tried all suggestions and the media doesn't appear either on the desktop (as it does with a CD) or from Places/home at all.

we've just been saving windows files to it but I can't find any cds which may have come with it.

a useful bit of information is that I'm using two external hard drives - one to run ubuntu and the other to access the files on seagate.  Any help?

---

### Post by coffeecat on 2009-03-25
> **samster500 said:**
> we've just been saving windows files to it but I can't find any cds which may have come with it.

I was thinking more of software that came ready installed on the USB drive. I have come across instances where this interfered.

> **samster500 said:**
> a useful bit of information is that I'm using two external hard drives - one to run ubuntu and the other to access the files on seagate. Any help?

I presume you mean you're booting up from a USB drive with Ubuntu. I've no experience of using USB installations, but if Ubuntu on a USB drive is failing to mount second USB drives, then this must be a bug.

One thing I forgot to ask. Have a you any other USB drive of any description? Can you beg or borrow one if not? A flash drive will do. If so, does this mount OK? If it doesn't then there is something screwy with your Ubuntu installation. If it does, then it must be down to something with the Seagate drive.

---

### Post by samster500 on 2009-03-25
There must be something wrong with Ubuntu because I've just plugged in a memory stick and it's been picked up immediately.

Thanks for all the help - I now give up.

---

### Post by coffeecat on 2009-03-25
> **coffeecat said:**
> A flash drive will do. If so, does this mount OK? If it doesn't then there is something screwy with your Ubuntu installation. If it does, then it must be down to something with the Seagate drive.

> **samster500 said:**
> There must be something wrong with Ubuntu because I've just plugged in a memory stick and it's been picked up immediately.

:-k :(

---

