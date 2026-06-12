---
title: "USB storage devices not mounted automatically"
date: 2010-08-14
forum: Desktop Environments
---

### Post by mindless1973 on 2010-08-14
Hi,

Ubuntu 10.04

Since a few weeks, I am experiencing a very annoying problem with USB mass storage devices. They are just not mounted automatically.

So, when I plug a device like an USB harddrive in, the /dev/sdx gets created, but no icons appears on my desktop. Now, I can mount it manually either via commandline or the Disk drive tool, but that is somehow annoying and also supporting applications (like F-Spot for disks holding pictures) are not started automatically.

Any idea how I can debug why those devices are not mounted in my userspace?

Thanks,

bye
Marcus.

---

### Post by Slurp on 2010-10-25
Just refloating this since I have this very problem with a brand new 10.10...

---

### Post by mindless1973 on 2010-10-25
> **Slurp said:**
> Just refloating this since I have this very problem with a brand new 10.10...

Hi,

It turned out that the root cause of the problem was actually the mount of SMB shares. Alltough the CIFS mount did succeed, the whole UDEV/MOUNT process somehow was confused.

When I removed the CIFS shares from my fstab, my system worked again as it should. Because I could not solve the CIFS problem, I migrated to nfs for remote file systems, since then I don't have any problems.

bye
Marcus.

---

### Post by Slurp on 2010-10-25
Thanks for your hint, now it's solved.

I looked into /etc/fstab and I realized that sdb1 was set as the swap partition... no idea why. I changed it to sda1 and now I have swap memory and usb automatic mounting for the same price.

---

