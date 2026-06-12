---
title: "Sometimes,when i started computer the thnuar will open some folders."
date: 2013-04-23
forum: Desktop Environments
---

### Post by cocoakekeyu on 2013-04-23
[B]Just like this:
[/B]
[IMG]http://t1.qpic.cn/mblogpic/ff47ff50d28dab1b068e/2000.jpg[/IMG]




[B]It's my fstab file:
[/B]```
# /etc/fstab: static file system information.#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sdb2 during installation
UUID=15ece3f9-075c-425e-a8c5-b9c80c7caf01 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda7 during installation
UUID=892db9fe-4723-499b-a01d-620381905e41 /home           ext4    defaults        0       2
# /dev/sda2&#25346;&#36733;&#22312;~/&#24037;&#20316;
UUID=3EAEFABDAEFA6CB1 /home/eve/&#24037;&#20316; ntfs uid=eve,gid=eve 0 0


# /dev/sda3&#25346;&#36733;&#22312;~/&#24433;&#38899;
UUID=D6A4CAA5A4CA8807 /home/eve/&#24433;&#38899; ntfs uid=eve,gid=eve 0 0


# /dev/sda6&#25346;&#36733;&#22312;~/&#22791;&#20221;
UUID=B6F4C3A0F4C3616B /home/eve/&#22791;&#20221; ntfs uid=eve,gid=eve 0 0


# /dev/sda1&#25346;&#36733;&#22312;~/MNT/&#31995;&#32479;&#20445;&#30041;
UUID=BC26649226645006 /home/eve/MNT/&#31995;&#32479;&#20445;&#30041; ntfs uid=eve,gid=eve 0 0


# /dev/sdb1&#25346;&#36733;&#22312;~/MNT/SYSTEM
UUID=A62A6A032A69D13B /home/eve/MNT/SYSTEM ntfs uid=eve,gid=eve 0 0


# /dev/sda5&#25346;&#36733;&#22312;~/MNT/GAME
UUID=4E66B6F466B6DBC1 /home/eve/MNT/GAME ntfs uid=eve,gid=eve 0 0



```

---

### Post by cocoakekeyu on 2013-04-30
help!

---

### Post by matt_symes on 2013-04-30
Hi

How do you have Thunar volume management configured ?

Open Thunar and from the menu

Edit => Preferences => Advanced Tab => Volume Management => Configure.

Check your settings there. That may be where the problem is.

Kind regards

---

### Post by cocoakekeyu on 2013-05-05
> **matt_symes said:**
> Hi

How do you have Thunar volume management configured ?

Open Thunar and from the menu

Edit => Preferences => Advanced Tab => Volume Management => Configure.

Check your settings there. That may be where the problem is.

Kind regards

Here:
[IMG]http://t1.qpic.cn/mblogpic/e3e71ae745dc6b80b74e/2000.jpg[/IMG]

But those are my hard disk, not the flash disk.

It is not always occur.

---

