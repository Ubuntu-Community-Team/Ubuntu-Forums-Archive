---
title: "Unable to boot. &quot;group descriptors corrupted!&quot; after hang and reset"
date: 2013-05-11
forum: Desktop Environments
---

### Post by Prakhar Mishra on 2013-05-11
Hello everyone,

It all started when my Ubuntu 12.04 hanged. After waiting it to respond for 15-20 mins, I resetted my machine. When I tried to boot it again, it opened busybox. I searched a little on this problem and found a solution i.e. "boot-repair". I installed it on Ubuntu 13.04 live USB and started a recommended repair.

It asks me to close all application using filesystem and close this window. After some operations, it asks me the same thing again and again. And now, I can't even see my grub. All I see is a "grub rescue>" terminal.

I tried to mount (from the GUI) the partition on which I was having my Ubuntu 12.04 from live CD but it says:-

```
Error mounting /dev/sda6 at /media/ubuntu/f982b86f-13d6-4040-bcfe-bd9e61917172: Command-line `mount -t "ext4" -o "uhelper=udisks2,nodev,nosuid" "/dev/sda6" "/media/ubuntu/f982b86f-13d6-4040-bcfe-bd9e61917172"' exited with non-zero exit status 32: mount: wrong fs type, bad option, bad superblock on /dev/sda6,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```

Here is the output of dmesg | tail:-

```
[11450.308988] EXT4-fs (sda6): ext4_check_descriptors: Checksum for group 0 failed (25444!=0)
[11450.308997] EXT4-fs (sda6): group descriptors corrupted!
[11460.126170] EXT4-fs (sda6): ext4_check_descriptors: Checksum for group 0 failed (25444!=0)
[11460.126176] EXT4-fs (sda6): group descriptors corrupted!
```

I also tried using testdisk. When I see my partition and press 'p' to list files, it says "No files found, filesystem may be damaged".

What should I do??

Regards,
Prakhar Mishra

---

### Post by gordintoronto on 2013-05-11
From your 13.04 LiveUSB, run Disks, point to your hard drive, see if it is healthy.

---

### Post by Prakhar Mishra on 2013-05-11
Hi gordintoronto,
Thanks for the reply. My disk's Assessment says:

Assessment: Disk is OK, 11 bad sectors (59° C / 138° F)

It says my disk is OK. But I don't know what so wrong with /dev/sda6.

---

### Post by Prakhar Mishra on 2013-05-12
Is there any way to repair my filesystem?

I don't have passkey for encriptfs. So recovering is not an option.

---

### Post by gordintoronto on 2013-05-12
Is this a laptop? 59 is awfully hot for a hard drive, I think your problem is due to your computer overheating. Cleaing might help, or maybe you need a cooler.

---

### Post by Prakhar Mishra on 2013-05-13
Is there no way out to recover my filesystem? At least give me a reply. Any one.....

---

