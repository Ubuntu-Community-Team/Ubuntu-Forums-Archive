---
title: "Cloning Ubuntu drive to Dual Boot System"
date: 2009-02-05
forum: General Help
---

### Post by tommygunner on 2009-02-05
I recently wanted to see how Ubuntu would work on my newer Windows based system. My current Ubuntu system is an older one running on an IDE based drive. I had 3 SATA drives in my Windows system so I took one of them out, installed in the old system, booted up Gparted, shrunk the ntfs partition and copied my Ubuntu partition to the unallocated space on the drive. I also set up the swap space for Ubuntu.

Next, I moved the drive back to the Windows system, restarted PC, went into BIOS and set this third drive as the primary drive for boot up.

It came up as "Error loading OS" or something of that nature. I'm assuming that because I also have ntfs data on this drive, the BIOS doesn't know what data to load.

I'm using the Oreilly article for ths: [http://www.linuxdevcenter.com/pub/a/linux/2006/05/08/dual-boot-laptop.html?page=3](http://www.linuxdevcenter.com/pub/a/linux/2006/05/08/dual-boot-laptop.html?page=3)

Next, I go into Gparted, open a terminal and copy the boot info to a file called UBUNTU.BIN. I then boot up into windows and copy the file to the C:\ drive. I do this, then go to the Control Panel startup stuff and under the boot file I add an entry for Ubuntu pointing the the file. I do this, then reboot but when I select Ubuntu all I see is a blinking cursor.

What could be the problem?

---

### Post by logos34 on 2009-02-05
sounds like you forgot to install grub to the MBR (?).  Use the 'restore' link in my signature.  Need to edit /boot/grub/menu.lst as well so it points to the new location for /, which now appears in second place after windows (i.e. 'root (hd0,1)')

---

### Post by tommygunner on 2009-02-05
Cool, I'll try that. I'll change the (hd0,0) items to (hd0,1) and see if it works. I'm not exactly sure how the numbering works. I have 3 hard drives in the system. Maybe it should be 2 instead of 1?

I probably have to work on changing the UUID also but will try this first.

---

### Post by logos34 on 2009-02-05
> **tommygunner said:**
> Cool, I'll try that. I'll change the (hd0,0) items to (hd0,1) and see if it works. I'm not exactly sure how the numbering works. I have 3 hard drives in the system. Maybe it should be 2 instead of 1?

grub starts counting beginning with '0'...If you install grub to the mbr of the same disk as ubuntu, and that's that one set as the boot disk (recommended) in the bios, then you want 'root (hd**0**,x)'
> 
I probably have to work on changing the UUID also but will try this first.

You shouldn't have to do that (since in your case it's been transferred to your new machine).  But if you want to you could use command

tune2fs -U random /dev/sdxy

then edit menu.lst and /etc/fstab

---

### Post by tommygunner on 2009-02-05
Thanks, 

I managed to get it working by installing grub on the MBR.

I think the reason my non-grub way didn't work was that I copied the UBUNTU file before I made changes to the menu.list.

It booted up and everything just fine. I updated the video driver and now I get nothing but that is another post thread.

---

### Post by mozkill on 2009-02-05
I would use the bootable Clonezilla CD instead (sorta like an open source version of Norton Ghost).  I think it will restore an image to a drive of a different size, if I remember correctly.

---

