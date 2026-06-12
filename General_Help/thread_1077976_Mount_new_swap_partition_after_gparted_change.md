---
title: "Mount new swap partition after gparted change"
date: 2009-02-22
forum: General Help
---

### Post by coolglobal on 2009-02-22
I have changed my partitions with gparted.

The swap was deleted and recreated and the primary partition was resized larger over another partition that was deleted.

Everything boots up fine. It is just that Conky is not seeing the New Swap Partition and giving a No Swap reading.

How do I mount the new swap partition permanently?

I am running a small custom install of Ubuntu with fluxbox.

---

### Post by taurus on 2009-02-22
When you resized or reformatted the swap partition, it's probably got a new UUID so you need to edit /etc/fstab and change the old UUID in there with the new one.

```
sudo blkid
```

---

### Post by caljohnsmith on 2009-02-22
How about doing this:
```
cat /etc/fstab | grep swap
cat /etc/initramfs-tools/conf.d/resume
```
If the UUID for the swap partition agrees in both those files, then copy/paste the swap UUID in those files to:
```
sudo mkswap -U [COLOR="Blue"]<UUID>[/COLOR] /dev/[COLOR="Blue"]sdaX[/COLOR]
```
And of course replace sdaX with your swap partition. After that, reboot, and let me know if you can use your swap partition again. You can always check with:
```
free
```

---

### Post by coolglobal on 2009-02-24
Everything is now back to normal, Conky sees the swap and *free* entered in Tilda detects the swap. Great. The method I did use was as suggested by Taurus. I did use the first two commands of caljohnsmith to see whats going on. Thank you kindly guys I really appreciate it. A little more info to help the next person searching this thread. To edit /etc/fstab you need to sudo your file manager for me the command was *sudo thunar*. Reboot to finish.

---

