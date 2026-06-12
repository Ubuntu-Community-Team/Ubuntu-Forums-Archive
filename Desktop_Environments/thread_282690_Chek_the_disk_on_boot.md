---
title: "Chek the disk on boot"
date: 2006-10-23
forum: Desktop Environments
---

### Post by hraposo on 2006-10-23
Ubuntu, on boot, check the disk avery 30 times of boots. I want disable this check. What can I do?

---

### Post by ansi on 2006-10-23
> **hraposo said:**
> Ubuntu, on boot, check the disk avery 30 times of boots. I want disable this check. What can I do?

turn off the following scripts: */etc/init.d/checkfs.sh* && */etc/init.d/checkroot.sh*.

You can do it, e.g., with ``*update-rc.d*''.

---

### Post by hraposo on 2006-10-23
How I use **update-rc.d**

---

### Post by Crc-3rr0r on 2006-10-23
Instruct the harddisk directly : use if you never want it fscked.
Remember its not just the number of mounts it's also the time interval too

for ext3 filesystems do :

tune2fs -c 0 /dev/[whereever your root partition is]
(count = 0 default=30 ie dont check filesystem after n mounts)

tune2fs -i 0 /dev/[whereever your root partition is]
(interval = 0 default=180days ie dont check filesystem after n days)

---

### Post by ansi on 2006-10-23
> **hraposo said:**
> How I use **update-rc.d**

It has a nice man-page:
```
man update-rc.d
```

>  Example of disabling a service:
          update-rc.d -f foobar remove

---

