---
title: "error on when i plugin my portal hard disk"
date: 2009-04-26
forum: General Help
---

### Post by StormRoBoT2 on 2009-04-26
hi, im having an error when i plug in my portal hard disk (NTFS) (file system)

is there any way i can read my hard drive?

the error is like on the attachment

---

### Post by StormRoBoT2 on 2009-04-26
i can plugin USB pendrive (FAT) file system

buy my external hard disk can't

please help :S

---

### Post by Screwdriver0815 on 2009-04-26
was the drive connected to another machine and not unmounted (= pulled the plug only)? 

If this is the case the easiest would be, to connect it to a windows machine, open the folder of the drive, close it again, unmount the drive  with "safely remove hardware" and try again with Ubuntu.

---

### Post by StormRoBoT2 on 2009-04-26
was the drive connected to another machine and not unmounted (= pulled the plug only)?  << i dont know what you mean by this

any way

i just format my USB hard disk(NTFS) format from windows

when i try to plug in to ubuntu the same error come out any suggestion?

---

### Post by Screwdriver0815 on 2009-04-28
> **StormRoBoT2 said:**
> was the drive connected to another machine and not unmounted (= pulled the plug only)?  << i dont know what you mean by this

any way

i just format my USB hard disk(NTFS) format from windows

when i try to plug in to ubuntu the same error come out any suggestion?

when you want to remove a USB-stick or a USB-Harddisk in Linux you always have to rightclick on the icon of the device on the desktop and have to choose "unmount device". 

The same in windows: you have to click on this small green arrow in the taskbar near the clock and to choose "safely remove hardware" and then choose the usb-drive.

Otherwise a flag on the usb drive will not be set, that the device is unmounted and Linux can not mount it again.

Thats what I mean with this. 

So if you format the harddrive and you do not do this (click on the green arrow and "safely remove hardware" and so on) the same state occurs again.

Thats what I wanted to make sure. And this is the only idea I have in this issue... :(

---

