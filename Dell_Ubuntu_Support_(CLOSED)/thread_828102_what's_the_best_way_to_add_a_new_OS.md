---
title: "what's the best way to add a new OS?"
date: 2008-06-13
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Fearless Freep on 2008-06-13
I have a 530n that was pre-installed with Ubuntu  and I recently got a free copy of Windows Vista at a recent Microsoft product demonstration.

 What would be the best way to add Windows Vista to my computer while keeping Ubuntu? 

 Is there some way give Vista its own SATA drive, not changing the drive containing Ubuntus  and then changing boot drives via bios to the OS I desire to boot? 

If I choose to make a duel boot system  must I install Vista first over my current Ubunto system and later Install Ubuntu because Ubunto will work with vista and not the other way around?

If both are possible, which is the better choice?


Are there any known issues with 530n hardware and standard Vista install discs?

---

### Post by logos34 on 2008-06-13
Another perfectly good Dell Ubuntu machine ruined... ;)

Kidding aside, at least you didn't have to PAY for windows.

If you want to dual boot vista to find out just how pathetic it really is, you should be able to do it on on a second drive no prob--either by toggling the bios boot order  as you say or using grub.  Sometimes grub can't do it, and if you'd prefer not having choose the drive each time in the Bios, you could alternatively use [EasyBCD]("http://neosmart.net/wiki/display/EBCD/Ubuntu").

There is [this howto]("http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm"), but unfortunately only covers dual-booting on single drive. However, the only difference is that you'd have to make sure the sata target drive is set first in the Bios hard disk boot order BEFORE beginning vista installation (otherwise windows will refuse to install).  Then add a windows entry (with [mapping]("http://users.bigpond.net.au/hermanzone/p15.htm#Windows_on_a_non-first_hard_disk")) to the bottom of /boot/grub/menu.lst, so that vista selection will appear on grub menu screen at boot.  Reboot and change the boot drive back to the linux hard disk.  If grub refuses to chainload vista, then you're left with either toggling the bios boot order or EasyBCD route.  

Back in ubuntu, add [vista partition with read-write access]("https://help.ubuntu.com/community/MountingWindowsPartitions?highlight=%28windows%29#head-c067eb7e3cd4107cc08cdf30a9e1aed8adb02971").

I found [this guide]("http://www.pctipsbox.com/dual-boot-vista-and-linux/") for two hard disks, but you shouldn't have to physically swap the drives.

---

### Post by mlsquad on 2008-06-13
It depends on what exactly you want out of Vista.  I need XP occasionally for school stuff, so I have it loaded into a virtual machine.  If you haven't played around with VMs  yet, simply run:
sudo aptitude install virtualbox-ose
You can then find the program in Applications->System.  Create a new machine, point the CD drive to your CD-ROM and pop in the CD.
VMs are not a good solution if you want to do things play Windows games, but for many other multi-OS solutions, it works great.

---

