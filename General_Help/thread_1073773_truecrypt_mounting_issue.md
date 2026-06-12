---
title: "truecrypt mounting issue"
date: 2009-02-18
forum: General Help
---

### Post by fubbe on 2009-02-18
hi,

i tried to mount my ntfs formated 250gb usb hdd using the following truecrypt(6.1a) command line. I used dmesg to check if sdb is my external hdd for sure. When i mount it with the gui it works out fine.

user@root:~$ sudo truecrypt --filesystem=ntfs-3g /dev/sdb /media/private -k /home/user/keyfile -p password

but i always get the following error.

Incorrect password or not a TrueCrypt volume.

any suggestions? :/

---

