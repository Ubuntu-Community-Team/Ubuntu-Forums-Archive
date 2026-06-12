---
title: "kernel panic"
date: 2009-02-09
forum: General Help
---

### Post by carrarin on 2009-02-09
I put ubuntu on my stick, and when i try to boot into it I get this error message:

Kernel Panic - Not syncing VFS Unable to mount root fs on unkown block (8,1)

What i really need is a simple solution to fix this, because i really have no idea what i'm doing.

---

### Post by LowSky on 2009-02-09
> **carrarin said:**
> I put ubuntu on my stick

I think you meant to say flashdrive

How did you, "put it on your stick"

---

### Post by carrarin on 2009-02-09
[http://www.pendrivelinux.com/ubuntu-810-persistent-flash-drive-install-from-live-cd/](http://www.pendrivelinux.com/ubuntu-810-persistent-flash-drive-install-from-live-cd/)

and 

[http://www.pendrivelinux.com/usb-boot-cd-for-ubuntu-810/#more-680](http://www.pendrivelinux.com/usb-boot-cd-for-ubuntu-810/#more-680)

I used the tutorials at pendrive linux.

Any help would be appreciated

---

### Post by carrarin on 2009-02-09
Does anyone know anything about the initrd file. and if it is, what would i have to do to fix it.

---

### Post by alphaniner on 2009-02-09
I recommend using unetbootin to create a bootable USB flash drive.  Read the guide [[COLOR="Red"]_here_[/COLOR]]("https://help.ubuntu.com/community/Installation/FromUSBStick").

---

### Post by carrarin on 2009-02-09
thats great, but i dont want to go through all that trouble, i just want to know if i can fix what  have already

---

### Post by carrarin on 2009-02-09
i think this might be happening 

monchichi:
"just out of curiousity, are you guys using sata or scsi hard drives, or something that would need modules loaded initially to detect the root filesystem? That would explain it, as initrd would handle the loading of those modules..."


how could i fix this

---

### Post by LowSky on 2009-02-09
> **carrarin said:**
> I put ubuntu on my stick, and when i try to boot into it I get this error message:

Kernel Panic - Not syncing VFS Unable to mount root fs on unkown block (8,1)

What i really need is a simple solution to fix this, because i really have no idea what i'm doing.
You don't know what your doing yet you think you know the answer...lol

> Kernel Panic - Not syncing VFS Unable to mount root fs on unkown block (8,1)
See this part it means that the flash drive was incorrectly setup as a bootable device, which means you need to recreate a bootable USB version of Ubuntu


> **alphaniner said:**
> I recommend using unetbootin to create a bootable USB flash drive.  Read the guide [[COLOR="Red"]_here_[/COLOR]]("https://help.ubuntu.com/community/Installation/FromUSBStick").

This is you best option

---

