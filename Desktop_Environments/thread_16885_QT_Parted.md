---
title: "QT Parted"
date: 2005-02-24
forum: Desktop Environments
---

### Post by sebdah on 2005-02-24
Hi!
I'm using QT Parted without problems on by Ubuntu-laptop. But now when I was going to learn a friend about it we met some problems.. We want to resize his primary Linux-partition. This is his partition tabel:

/dev/hda1  ext3  Active
and a swap..

When we right-click on the partition we aren't able to choose "Resize" (it grey..). Why it that?

Very thankful for answers

---

### Post by tim1 on 2005-02-24
Maybe you can't resize /dev/hda1 because your operating system is running on it and  is therefore mounted. Try booting with a live cd and resize it from there,

If it is a problem of qparted, you could try gparted, another partitioning tool that has a nice gtk2 gui. 

greets, tim

---

### Post by sebdah on 2005-02-24
thank you for the tip.. I'll make a try and come back here again!

---

