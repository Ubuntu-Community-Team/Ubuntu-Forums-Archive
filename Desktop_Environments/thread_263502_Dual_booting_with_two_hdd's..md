---
title: "Dual booting with two hdd's."
date: 2006-09-23
forum: Desktop Environments
---

### Post by pyro666 on 2006-09-23
Hello,

I have two SATA HDD's.

I currently run Windows XP on my primary HDD, i added another SATA hdd to my system and am wanting to install ubuntu onto it and have the dual boot option between both hdd's.

Now i have installed ubuntu but no modifications have been made to the MBR and just continues to boot to windows XP.

Some advise would be excellent.

Thanks,
Grant

---

### Post by KeithO on 2006-09-23
are you certain you installed ubuntu?  sounds almost like you just ran the live cd.  grub would have been installed on the master mbr and you'd have an option as to which os to use.

---

### Post by Dangling on 2006-09-23
I had my ubuntu installed on an external hard drive. I didn't change my MBR. I went into the BIOS and made the usb drive boot first. If your second hdd is internal, you should have an option in the BIOS to boot from that first. 

If you still have trouble (GRUB not loading error msg), check if your boot partition in the beginning of the drive. You should be able to set up the boot partition in the manual install. 

Hope this helps.

---

### Post by Dangling on 2006-09-23
Also you might want to check out this thread :

[http://www.ubuntuforums.org/showthread.php?t=179902](http://www.ubuntuforums.org/showthread.php?t=179902)

---

