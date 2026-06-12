---
title: "mount encrypted partition"
date: 2009-06-09
forum: General Help
---

### Post by GSMX on 2009-06-09
hi all,

A few days ago, my laptop broke down, probably a problem with the internal power supply, but FUBAR anyway.

So I bought a new laptop, but now my problem:
The original laptop had two drives:
-sda
[INDENT]-sda1: "PQSERVICE"-partition (Win recovery partition)[/INDENT]
[INDENT]-sda2: Windows Vista[/INDENT]
[INDENT]-sda3: Ubuntu 9.04 Root (ext4)[/INDENT]
-sdb
[INDENT]-sdb1: Ubuntu encrypted /home[/INDENT]
[INDENT]-sdb5(?): Swap[/INDENT]

I don't care at all about the contents of drive sda1, but I do about sdb. I bought a sata-usb-case for sdb, but how can I mount this encrypted volume? AFAIK I used all default settings of the amd64 alternate cd and I think I still know the used passprase, or, so I hope :)

But how can I mount this partition?

---

### Post by GSMX on 2009-06-11
bump

---

### Post by GSMX on 2009-06-15
2nd *bump*

I can hardly find any information on this subject, looks like almost nobody encrypts his/her drive... :-(

---

### Post by GSMX on 2009-06-21
3rd *bump* 

still no joy

tried "sudo -t ecryptfs /dev/sdb1 /mnt/drive"
No luck, it says "device unknown (20)"

---

### Post by michy99 on 2009-06-21
If you are mounting it by usb, I don't think it will be sdb1 any more.

---

### Post by GSMX on 2009-07-07
according to /dev/sdb it is

---

### Post by AnotherDave on 2009-07-07
The lack of information on this subject is discouraging!

You have to map the partition 
```
sudo cryptsetup luksOpen /dev/sdb1 foo
```
then create a mount point
```
sudo mkdir /media/foo
```
then mount
```
sudo mount /dev/mapper/foo /media/foo
```

This should let you access the data on the HD. As for the USB port and integrating this into your new system... I'm waiting for a good article on this myself!

---

### Post by GSMX on 2009-07-07
thanks for giving the first informative answer :D

though it didn't help:
```
sudo cryptsetup luksOpen /dev/sdb1 foo
Enter LUKS passphrase: 
Command failed: No key available with this passphrase.
```

while i'm certain i used the right passphrase... :(

---

### Post by AnotherDave on 2009-07-07
The answer is probably in here:

[http://linux.die.net/man/8/cryptsetup](http://linux.die.net/man/8/cryptsetup)

though darned if I understand it. Suerte!

---

### Post by AnotherDave on 2009-10-25
I see that nobody's jumped in with more information. I think you'll like this:

[http://wiki.archlinux.org/index.php/LUKS_Encrypted_Root](http://wiki.archlinux.org/index.php/LUKS_Encrypted_Root)

---

