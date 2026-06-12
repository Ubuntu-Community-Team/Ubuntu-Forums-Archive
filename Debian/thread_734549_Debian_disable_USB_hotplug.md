---
title: "Debian disable USB hotplug"
date: 2008-03-24
forum: Debian
---

### Post by PurposeOfReason on 2008-03-24
I have a server that I recently put Debian minimal on. Is there a way to disable the hotplugging in the usb devices? I'd like to use them to charge my ipod and whatnot but if they get mounted I don't want the chance of just ripping them out and losing data.

---

### Post by kerry_s on 2008-03-24
huh? 
debian minimal doesn't auto mount. you would have to install like ivman or have a file manager that does that through hal.

i use pmount on mine using rox with a fstab entry for usb(sda1).

---

### Post by PurposeOfReason on 2008-03-24
Maybe I just think it did because I had a USB thumb drive in when I booted (during installation) which would then get mounted?

---

### Post by kerry_s on 2008-03-24
> **PurposeOfReason said:**
> Maybe I just think it did because I had a USB thumb drive in when I booted (during installation) which would then get mounted?

it shouldn't, it would only be detected but not mounted, unless you have a fstab entry with "auto" in it. the only way it would mount is if you mount it> su && mount -t vfat /dev/sda1 /media/usb
something like that.

---

