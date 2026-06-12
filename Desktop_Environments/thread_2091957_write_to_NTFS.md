---
title: "write to NTFS"
date: 2012-12-06
forum: Desktop Environments
---

### Post by Toriku on 2012-12-06
Anyone know how to get linux to write to a HDD with a NTFS filesystem? I'm sure I saw a Linux box writing to NTFS before, it was running Samba, and Apache... OS was on its own flash memory, with a hard disk in NTFS for mass storage...

---

### Post by leclerc65 on 2012-12-06
Install then run ntfs-config. Tick on the boxes 'enable read' , 'enable write'.

---

### Post by Morbius1 on 2012-12-06
> Anyone know how to get linux to write to a HDD with a NTFS filesystem?If you mounted the ntfs partition though Nautilus Linux writes to ntfs by default and has since Hardy.

Are you having it automount through fstab? If you are post the output of the following command:
```
cat /etc/fstab
```If you want it to please post the output of this command:
```
sudo blkid -c /dev/null
```> I'm sure I saw a Linux box writing to NTFS before, it was running Samba, and ApacheThat's an entirely different question. Are you talking about writing to a samba share of an ntfs partition located on a Linux box or accessing an ntfs partition on a Windows box.

I guess this boils down to I don't understand the nature of the problem since I don't know where this ntfs partition is located and how you are trying to write to it..

---

