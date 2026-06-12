---
title: "USB Hard drive not mounting at boot"
date: 2009-04-27
forum: General Help
---

### Post by diilbert on 2009-04-27
I have a usb hard drive hooked up to my box for backup.  It does not mount when I reboot the machine, but if I run

```

mount /mnt/usbhdd

```

it mounts fine.

Here is the line I have in fstab:

```

/dev/sda1       /mnt/usbhdd     ext4    rw,user,noauto  0       0

```

Any thoughts would be appreciated.

Thanks!

---

### Post by kpkeerthi on 2009-04-27
Is it an ext4 formatted partition?

What does the below command print?
```
sudo mount -a
```
Post back the errors.

---

### Post by bacardiandwatermelon on 2009-04-27
Try removing it from you fstab file and restarting, I've always had better luck with ubuntu controlling my external devices..

---

### Post by uncle-c on 2009-04-27
> **diilbert said:**
> 

Here is the line I have in fstab:

```

/dev/sda1       /mnt/usbhdd     ext4    rw,user,noauto  0       0

```

Any thoughts would be appreciated.

Thanks!

**noauto **means that it will not be mounted at bootup. Replace this with **auto**

---

### Post by melgish on 2009-04-27
Not sure if this is the same issue, or just the same symptoms.

Over the weekend, I upgraded my VMWare host to Ubuntu 9.04 (64bit) from 8.10 (32bit), and started using ext4 for the whole drive. (it's one big partition, yes I know that's bad)

Anyway, on startup, the system drops to a shell, saying it can't find drive UUID='the correct guid for my USB drive'

Watching the console, I see the drive detected about 5-10 seconds *after* the halt, and at this point mounting the drive manually succeeds, and I can continue booting.

So, the problem is that fstab is processed before all the USB devices are online.

The question is how can it be delayed?  I don't want to have to go to the console every time I restart (not that it happens all that often)

---

### Post by diilbert on 2009-04-27
> **uncle-c said:**
> **noauto **means that it will not be mounted at bootup. Replace this with **auto**

Thanks!  Was exactly what I was looking for.

---

