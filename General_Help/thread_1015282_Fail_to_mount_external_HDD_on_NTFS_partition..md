---
title: "Fail to mount external HDD on NTFS partition."
date: 2008-12-18
forum: General Help
---

### Post by cikson on 2008-12-18
When I try to mount external HDD on NTFS partition, I got this:
```
$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sdb1': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sdb1 /mnt/ -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sdb1 /mnt/ ntfs-3g force 0 0

```
Same with ```
sudo mount /dev/sdb1 /mnt/
```
Thank you in advance! :D

---

### Post by Crafty Kisses on 2008-12-18
What happens when you try running the following command?
```
sudo mount -a
```

---

### Post by dorkdork777 on 2008-12-18
It gives you the required line in the error message. ;)

```
mount -t ntfs-3g /dev/sdb1 /mnt/ -o force
```

This confused me the first time I got that at first, before I noticed that :P but could someone else confirm this is right? I don't want to go leading someone down the wrong path :/

---

### Post by cikson on 2009-01-26
This works: 
```
mount -t ntfs-3g /dev/sdb1 /mnt/ -o force
```
The problem was in unmounting HDD on Windows withot 'Safely Remove Hardware'.

---

