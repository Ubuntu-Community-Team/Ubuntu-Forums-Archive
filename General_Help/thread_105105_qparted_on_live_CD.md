---
title: "qparted on live CD"
date: 2005-12-17
forum: General Help
---

### Post by dc2447 on 2005-12-17
On the live CD is qparted available?  I want to resize an NTFS partion to dual boot a laptop but as I have never dual booted before I'm a bit lost about resizing the existing partition.

Thanks in advance

---

### Post by Iandefor on 2005-12-17
It may have Gparted. If you really want QTParted (I believe you might have meant that) you can run it from [Knoppix]("http://www.knoppix.org/"). Alternatively, you can run it from the [System Rescue CD]("http://www.sysresccd.org/"). But I don't know if QTParted comes with the LiveCD.

---

### Post by aysiu on 2005-12-17
If the live CD doesn't have gparted on it, you can always install it (it won't really "install" anywhere except temporarily in your computer's RAM).

Once you boot the live CD, open a Konsole terminal and type ```
sudo apt-get update
sudo apt-get install gparted ntfsprogs
gparted
``` If you want QTParted, you can install that, too, but you'll have to enable extra repositories for that.

---

