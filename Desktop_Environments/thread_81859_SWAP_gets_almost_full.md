---
title: "SWAP gets almost full"
date: 2005-10-25
forum: Desktop Environments
---

### Post by kurtkraut on 2005-10-25
I have 256mb 33mhz DDR installed in my computer and I've partitioned a SWAP partition on 256mb. With about 10h turned on, my swap gets about 88% fulled and the system get slower.

What should I do to avoid swap and/or have a better performace beyond installing more RAM ?

---

### Post by stuporglue on 2005-10-25
Do you have more HD space? You can create a swap file.

See [http://wiki.ubuntu.com/LiveCDCustomizationHowTo](http://wiki.ubuntu.com/LiveCDCustomizationHowTo) near the top of the page. "If you don't have enough swap". 

You could also switch from some of the more intensive programs you may use to lighter weight ones like Gnome-->Xfce, OpenOffice.org Writer --> Abiword, etc.

---

### Post by kurtkraut on 2005-10-25
sudo dd if=/dev/zero of=/tmp/swap bs=1M count=3000

This will make a swap file of 3gb !?

---

### Post by metoo on 2005-10-26
What's eating up your memory?

Checked with top or (exmap ?) ?

---

