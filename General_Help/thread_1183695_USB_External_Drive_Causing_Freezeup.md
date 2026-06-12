---
title: "USB External Drive Causing Freezeup"
date: 2009-06-10
forum: General Help
---

### Post by videomax on 2009-06-10
When I plug my external USB Hard drive into my computer, ubuntu detects it and mounts it. However, whenever I attempt to access the drive via terminal or the gui, the programs lock up and freeze. I can see from my USB device that nothing is happening to the drive, as the hard drive activity LED doesn't switch on. The drive is formatted FAT32, and I can access it fine from windows. I am using ubuntu 8.10 btw.
Can you help me?

---

### Post by videomax on 2009-06-10
bump

---

### Post by merlinus on 2009-06-10
Exactly what are you trying to access from the external drive?

---

### Post by videomax on 2009-06-10
I am just trying to browse the drive contents. I click on the dekstop link to it, but nothing comes up.

I do cd /media/MyBook/ in terminal, and then if I type ls or TAB terminal just freezes.

---

### Post by merlinus on 2009-06-10
Can you navigate to the drive from nautilus?

---

### Post by videomax on 2009-06-10
No I cannot.

---

### Post by videomax on 2009-06-10
Also, I have noticed that when I share the drive to other computers vis NFS, sometimes they will come up with a "stale NFS error", even though I haven't removed or renamed the shared folder.

---

### Post by merlinus on 2009-06-10
You might try running nautilus as root to see if you can access the drive:

```

gksu nautilus

```

---

### Post by videomax on 2009-06-10
This is not a permission problem. The drive is not even being accessed, I can tell because the LED blinks on hard disk activity, and it does not do that when I attempt to change directories to it.

Do you think upgrading to 9.04 will fix it?

---

### Post by merlinus on 2009-06-10
iirc, vfat does not use permissions.  But I can't imagine that upgrading to 9.04 would change anything.  The problem lies elsewhere.

I have run across a few other posts, however, detailing difficuties with external usb drives.  Have you tried plugging it into different ports?

Also, what does this show:

```

lsusb

```

---

### Post by videomax on 2009-06-10
I rebooted again. and it seems to be working . . . 

weird.

(this was after I had already tried rebooting twice earlier in the day)

---

### Post by merlinus on 2009-06-10
Ain't computers grand!!!

Glad it is working.  Sometimes the usb ports get screwed up due to conflicts, and rebooting will fix it.

---

