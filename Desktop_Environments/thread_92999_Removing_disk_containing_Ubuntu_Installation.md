---
title: "Removing disk containing Ubuntu Installation"
date: 2005-11-21
forum: Desktop Environments
---

### Post by CaKiwi on 2005-11-21
I installed Ubuntu to dual boot from a second disk and now I want to remove that disk to temporarily install another disk that has some data I need. But when I remove the Ubuntu disk, Grub gets an error and I cannot boot. How can I temporarily disable grub. Also, how do I modify the boot order in Grub.

Thanks in advance

CaKiwi

---

### Post by aysiu on 2005-11-21
The problem is that even though Grub lives on the MBR, the configuration for Grub lives on your Ubuntu hard drive (the one you're trying to remove). Can you temporarily remove the first disk instead of the second one?

---

### Post by CaKiwi on 2005-11-21
aysiu,

No, not easily, because it contains [SIZE="1"]WinXP[/SIZE]  that I want to boot to access the new disk

---

### Post by aysiu on 2005-11-21
[QUOTE=CaKiwi]aysiu,

No, not easily, because it contains [SIZE="1"]WinXP[/SIZE]  that I want to boot to access the new disk[/QUOTE] You can access the new disk from Ubuntu. What kind of disk is it? Ubuntu can access NTFS (read only) and FAT32 (read/write).

---

### Post by CaKiwi on 2005-11-21
The disk is NTFS and I want to read and write it. I am solving the immediate problem by getting an external USB disk enclosure. But it looks like there is no simple to remove my second disk and if I lose either disk I will not be able to boot my system. Is there a way to put all the information grub needs on the first disk?

Also, how do I change the boot order in Grub?

---

### Post by aysiu on 2005-11-21
Why does it matter if you change the boot order in Grub? If the Grub configuration lives on the second drive, it won't matter if you default the order to boot from the first drive.

Instead of talking about the **methods** by which you're trying to accomplish a task, why don't you describe **the task itself**.

Why do you need to write to this new NTFS drive? Is the information something you need to copy somewhere or do you need to modify files on that drive? How big are all of these drives (all three of them) in terms of GB?

Please, be as specific as possible about what you're trying to accomplish. You may not be going about it the easiest way.

---

### Post by CaKiwi on 2005-11-21
The original task was to take a friend's 60GB NTFS disk, install it in my system as a second disk and copy files off it onto a DVD. This task is no longer needed because my friend has decided to buy an external disk enclosure and attach the disk to his new system as a backup. When I was preparing for this task, I discovered that if I removed my second (80GB) disk I could no longer boot my system to Windows XP and I wondered if there was some around this. 

The question about the "boot order" is completely separate. Everyone else who uses my computer wants to use windows. How do I make Windows the default operating system?

Thanks for your assistance

CaKiwi

---

### Post by aysiu on 2005-11-21
For the original task, read-only access would have worked (as you were simply copying files, not modifying them). Well, I guess it's a moot point now.

To edit the boot default, type this in a terminal ```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_backup
sudo nano /boot/grub/menu.lst
``` Scroll through the code until you find a line that says ```
default 0
``` What that really means is default choice is the first (or 0-th) entry. That entry is probably Ubuntu.

So find the Windows entry (let's say, for the sake of this example, that Windows is your fourth entry). You just change it to say ```
default 3
``` Then save the file (control-x), confirm the save (y), and exit nano (enter).

That's it.

---

### Post by tommythecat on 2005-11-21
I could be wrong but this sounds like an issue that may only be fixed by booting to alternative media like a floppy or bootable CD, or installing a different bootloader.

His MBR is on disk0 and his grub.conf is on disk1, which makes him dependent on both disks to boot, unless a different bootloader, or bootable media is used.  A windows XP boot disk could be used if you have one.

Again I could be wrong or maybe I'm missing something, but that is what it sounds like to me.

Edit:
Oops I jumped the gun and added confusion to an issue that aysiu already addressed.  Sorry I'll read more completely before posting from now on.

---

### Post by CaKiwi on 2005-11-21
aysiu,

Thanks a lot for your assistance,  I've now got the boot default working as I want it.

tommythecat,

I think I need to work out a recovery plan along the lines you suggest. If I have a good plan hopefully I will never need it.

CaKiwi

---

### Post by tommythecat on 2005-11-22
How large is your largest drive?  If it is big enough your best bet is to install it as your primary internal drive,  partition it and run all of your OS's off of it.

---

### Post by CaKiwi on 2005-11-24
My master drive is large enough to run both WinXP and Ubuntu. So now I need advice on how to go about partitioning it. What is a reasonable size for the Ubuntu partition? Do I need to do this before installing Ubuntu? When I first installed Ubuntu, the only options I recall were to use all the disk or use all the free space. Is there a way to specify a partition size during installation?

Thanks in advance.

---

### Post by tommythecat on 2005-11-24
I am pretty sure that the native windows XP disk management will not allow you to decrease a partition size, so you will likely need a 3rd part tool , or else you can use fdisk and start from scratch if you dont mind reinstalling windows. 

I generally do all of my partitioning with Acronis Disk Director, but they want $50 for the new versions of it now.  There are quite a few other tools out there that will allow you to reduce the size of an existing partition, but the only one I've used is acronis, so I have no other reccomendations.  You may want to look around at used ostfware places or on ebay and see if you can find an old copy of partition magic nice and cheap.

What I do generally is create a partition that is half the total size of the drive, then I install windows on it.  If you want you can also create a small fat32 partition for read/write access to a single partition from both linux and windows.  Then I will setup linux in the remaining free space.

---

