---
title: "Ubuntu and Windows"
date: 2006-07-28
forum: Desktop Environments
---

### Post by dareofficer on 2006-07-28
I would like to have a dual boot system.  I put a slave hard drive on, so I can put Windows on it.  I have Ubuntu on my master hard drive.  I tried to install Windows on the slave hard drive but it said I have to put some information on the master.  Could someone please explain what I have to do?

Will I loose my Ubuntu?  Will this make a Grub problem?  I have read in the forums that installing Ubuntu first then Windows will not work.  

Thanks

---

### Post by Tomosaur on 2006-07-28
> **dareofficer said:**
> I would like to have a dual boot system.  I put a slave hard drive on, so I can put Windows on it.  I have Ubuntu on my master hard drive.  I tried to install Windows on the slave hard drive but it said I have to put some information on the master.  Could someone please explain what I have to do?

Will I loose my Ubuntu?  Will this make a Grub problem?  I have read in the forums that installing Ubuntu first then Windows will not work.  

Thanks
Windows will overwrite your master boot record to **ignore** your linux install, but it will not delete it. Either way, windows does not let you access your linux partition since it's not NTFS or FAT32. If you install windows second, then yes, grub will disappear, and you will not be able to access linux at all.

Some say you can reinstall grub using the Ubuntu install CD, by choosing the 'manually partition' but not performing any partition options. I wouldn't recommend that method though, since it may go wrong and you could lose your data.

I would recommend giving [GAG](http://gag.sourceforge.net/) a try. It's a graphical bootloader which runs from a floppy disc but can later be installed to your hard drive if it works.

However, the easiest way to avoid this mess is to install windows first, and then linux.

Oh yeah, there is also a way to use the windows boot manager to boot into linux. [Here is more info](http://www.tprthai.net/bootmgr.htm). Could be worth a shot.

---

### Post by TheBlackNoodle on 2006-07-28
Grub will be overwritten, but you can fix it with the Live CD in a terminal pretty easily.

Try this link:
[http://ubuntuguide.org/wiki/Dapper#How_to_restore_GRUB_menu_after_Windows_installation](http://ubuntuguide.org/wiki/Dapper#How_to_restore_GRUB_menu_after_Windows_installation)

---

### Post by dareofficer on 2006-07-31
Thanks, it is working perfect now.

---

