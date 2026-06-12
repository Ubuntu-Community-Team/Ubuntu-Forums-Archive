---
title: "Need quick GRUB support"
date: 2006-07-30
forum: Desktop Environments
---

### Post by uber on 2006-07-30
I accidently changed a bunch of stuff around in my grub config files. Now I can't mount the drives to boot. I booted up with the live cd, so how can I access my drive to correct what I have done?

---

### Post by Dubbayoo on 2006-07-30
interrupt the boot process and edit the boot command line to correct what you changed. I changed my boot device by mistake once.

---

### Post by uber on 2006-07-30
How can I do that? (What commands, ect.)

---

### Post by uber on 2006-07-30
Is there any way at all I can mount my drive from the livecd? If I could do that, I could simply edit the files and undo what I have done. I just don't know how to mount my disk.

If it helps, I posted the results of the sudo fdisk -l command below.

Disk /dev/hdc: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1        9728    78140128+   7  HPFS/NTFS

Disk /dev/hdd: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1   *           1       24321   195358401    7  HPFS/NTFS

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19079   153252036   83  Linux
/dev/sda2           19080       19457     3036285    5  Extended
/dev/sda5           19080       19457     3036253+  82  Linux swap / Solaris

---

### Post by uber on 2006-07-30
I fixed it by mounting /root.

---

### Post by ButteBlues on 2006-07-30
Just in case of future mishaps, you might want to google up how to bootstrap Linux via GRUB (ie. booting entirely from commandline).

---

### Post by uber on 2006-07-30
Thanks, I'll look into that.

---

