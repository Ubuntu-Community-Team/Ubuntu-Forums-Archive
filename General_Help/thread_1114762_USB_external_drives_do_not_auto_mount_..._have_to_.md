---
title: "USB external drives do not auto mount ... have to go through terminal"
date: 2009-04-03
forum: General Help
---

### Post by Stop-state-terrorism on 2009-04-03
Hi,

On kubuntu 8.10 (was on ubuntu too)

I have to use *sudo mount *in terminal to have my keys recognized ...


here is my config (last line)

proc /proc proc defaults 0 0
# Entry for /dev/sda5 :
UUID=34407750-5d4e-4cee-bdc1-7169abecde5a / ext3 relatime,errors=remount-ro 0 1
# Entry for /dev/sda6 :
UUID=cad86dda-b7b3-432d-b6a4-bef4811cc631 none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/sda1 /media/GNR-hd ntfs-3g defaults,locale=fr_FR.UTF-8 0 0
**/dev/sdb1 /media/ExternalUSB ntfs-3g locale=fr_FR.UTF-8 0 0**

i tried do have *defaults* too for the last line, no luck.

Any idea?

---

### Post by vpsville on 2009-04-03
Whats in your /etc/fstab?

Try:
/dev/sdb1/media/ExternalUSB ntfs-3g locale=fr_FR.UTF-8,defaults 0 0

---

