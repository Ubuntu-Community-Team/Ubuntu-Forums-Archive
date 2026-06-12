---
title: "Grub 17"
date: 2009-04-28
forum: General Help
---

### Post by gloken on 2009-04-28
Hi, 

I recently had my harddrive crash during a distro upgrade. I was unable to mount the drive or interact with it at all. I ran fsck to repair the disk, and the process completed. 

When I attempt to boot the system now, I receive a GRUB error 17.

I desperately want to salvage any data I can from the disk, does anyone know where I could go from here?

---

### Post by phinullfermata on 2009-04-28
It could be a problem with your boot menu. To edit it to what you need, use a live cd to access the partition already in your computer, and edit '/boot/grub/menu.lst'.  I'm not very familiar with the boot menu, just what I had to do to fix the same error, so hopefully someone else can help with that.

Alternatively, if you just want to salvage data, the live CD is great for that as well, because as long as the partition is there it can access it and copy files to another location.

Hope this helps :)

---

### Post by gloken on 2009-04-29
> **phinullfermata said:**
> It could be a problem with your boot menu. To edit it to what you need, use a live cd to access the partition already in your computer, and edit '/boot/grub/menu.lst'.  I'm not very familiar with the boot menu, just what I had to do to fix the same error, so hopefully someone else can help with that.

Alternatively, if you just want to salvage data, the live CD is great for that as well, because as long as the partition is there it can access it and copy files to another location.

Hope this helps :)

Well, I managed to get the drive mounted off the boot cd. I'm frankly not sure what changed, but I got it mounted and that's what counts.

Now it's on to data recovery. BLEH.

Thanks for the response!

---

