---
title: "USB doesn't work"
date: 2009-01-24
forum: General Help
---

### Post by arturus on 2009-01-24
Hi.
I have 4 partition  and I tried to automount one of them. I added to my fstab file following code:
```
UUID="42fc4834-f5ad-4e1e-ab8f-47baaa0d34c8"
/dev/sda3       /mnt/data               ext3    defaults 0       1
```

Partition is mounted ok, but after this my usb doesn't work. Do you have any ideas?

---

### Post by diablo75 on 2009-01-24
> **arturus said:**
> Hi.
I have 4 partition  and I tried to automount one of them. I added to my fstab file following code:
```
UUID="42fc4834-f5ad-4e1e-ab8f-47baaa0d34c8"
/dev/sda3       /mnt/data               ext3    defaults 0       1
```

Partition is mounted ok, but after this my usb doesn't work. Do you have any ideas?

Doesn't look like anything in that code should cause your USB ports to stop working, although I would think you'd want your mount point to be in your /media/ folder instead of /mnt/ (but it probably works just the same).

What are your trying to use via your USB port that's not working?

---

### Post by arturus on 2009-01-24
I tried use external disk and pendrive's. This is no problem with mounting folder, because before format i mounted disk in /media/data

But my mouse is working ok.

---

### Post by taurus on 2009-01-24
> **arturus said:**
> 
```
UUID="42fc4834-f5ad-4e1e-ab8f-47baaa0d34c8"
/dev/sda3       /mnt/data               ext3    defaults 0       1
```


The entry for /dev/sda3 in /etc/fstab should look like this

```
UUID=42fc4834-f5ad-4e1e-ab8f-47baaa0d34c8   /mnt/data   ext3    defaults    0    1
```

or

```
/dev/sda3       /mnt/data    ext3    defaults    0       1
```
but not the way you have right now.

---

### Post by arturus on 2009-01-24
Ok, I will try like you say for a sec, because I'm installing WindowsXP:)

---

### Post by taurus on 2009-01-24
If you're installing windows on a machine that already has Ubuntu, windows will wipe out GRUB from the MBR which means you won't be able to boot Ubuntu anymore.  Therefore, you have to use Ubuntu LiveCD to reinstall GRUB to MBR so you can boot both.

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by arturus on 2009-01-24
It's working:D Cheers, it was so easy

I know about grub and windows. I using Virtualbox to install Windows, because my computer is too new and Windows can't found drivers for my hardware:)

Cheers one more time:)

---

