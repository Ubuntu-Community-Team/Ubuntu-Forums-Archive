---
title: "how can i change the disk space of windows and Ubuntu?"
date: 2009-02-11
forum: General Help
---

### Post by x88a on 2009-02-11
i have 80gb
windows xp takes 40gb
ubuntu 8.04 takes 40gb

how can i change it to
windows xp 60gb
ubuntu 20gb

tq

---

### Post by 7mkgw7q on 2009-02-11
Dual boot or using Wubi?

---

### Post by 7mkgw7q on 2009-02-11
If dual boot, I would recommend booting to live cd and using gparted. Are you familiar with it? Let me know whether this works or if you use Wubi. If you are unfamiliar with gparted, let me know and I will help you out.

---

### Post by x88a on 2009-02-11
i have not done much with my Linux yet (so i dont really care if i lose any info in it)
is it possible to just transfer some Linux disk space to my windows using some program?

---

### Post by NTolerance on 2009-02-11
Remember to always back up all your data before resizing partitions.

---

### Post by 7mkgw7q on 2009-02-11
yes, boot from the live cd (cd you installed with was most likely a live cd) and choose to run without installing. This guide I am linking below may help you. You should be able to resize it without too much grief.

[https://help.ubuntu.com/community/HowtoPartition/ResizingPartition](https://help.ubuntu.com/community/HowtoPartition/ResizingPartition)

Edit: That is very true about remembering to back up your files before resizing.

---

### Post by x88a on 2009-02-11
ok, i will give it a try when i am back to my ubuntu machine
thanks

---

### Post by 7mkgw7q on 2009-02-11
Let me know if you have any problems and I will see what I can do.

---

### Post by geirha on 2009-02-11
As 7mkgw7q mentioned. You need to specify how Ubuntu is installed because the way to resize your partitions will differ depending on how you installed it. Did you install it in windows (WUBI) or did you boot the Ubuntu CD and install it from there?

If the latter is the case, then this page should have the instructions you need: [https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition) 

In particular you should read the Partitioning Basics page and then the Resizing A Partition page.

EDIT: err, I'm too slow :)

---

### Post by x88a on 2009-02-17
i wish to transfer 20GB from sda4 (home) to sda1 (windows)
i tried to unmmount sda4, but it says the device is busy
how should i proceed?

---

### Post by x88a on 2009-02-17
attached are my partitions

---

### Post by geirha on 2009-02-17
You cannot do that from inside the installed Ubuntu, you'll need to boot the Ubuntu CD and partition from there. You'll find gparted under System -> Administration -> Partition Editor.

---

