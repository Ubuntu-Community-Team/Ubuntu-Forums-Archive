---
title: "Updating grub for US 9.04 and Fed11"
date: 2009-06-22
forum: General Help
---

### Post by salvachn on 2009-06-22
I have Ubuntu 9.04 Desktop installed on a 250GB SATA disk alongside XP. I have an old 40GB IDE disk in which I've installed Ubuntu Server 9.04 and Fedora 11 on two ext3 partitions. But both of these installations didn't recognise my Ubunu Desktop install, and so I boot into my 250 GB for Ubuntu and XP and the 40GB for Fedora 11. I cannot login to US 9.04 too. I tried blkid and editing grub, but it wouldn't work. Any idea how to update Ubuntu Desktop's grub to let me select all 4 installations?

---

### Post by Soul-Sing on 2009-06-22
I [COLOR="Red"]think[/COLOR] (not sure though) you have to update grub via ```
sudo grub
``` from a live-cd.
[COLOR="Red"]example[/COLOR] typ: Typ root (hd0,0) if your linux part. is on sda1
             Typ root (hd0,5) if your linux part. is on sda6

Then typ: setup (hd0) enter
Then: quit  enter

But please be careful, maybe some other members have additional information, or do a ```
man grub
```

---

### Post by Tipped OuT on 2009-06-22
I've never used Fedora before, but I know with Ubuntu, if you boot into recovery mode, you can automatically update Grub, I believe.

---

### Post by salvachn on 2009-06-23
Thanks. Recovery mode worked.

---

