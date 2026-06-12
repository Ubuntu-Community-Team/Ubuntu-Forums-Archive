---
title: "dual boot to single boot"
date: 2012-10-24
forum: Desktop Environments
---

### Post by hozmaster on 2012-10-24
Hi everybody,

I would like turn my dual boot just to boot only Ubuntu and turn  my Windows Vista installation to start in Virtualbox.

Is there good instructions for that ?

---

### Post by 2F4U on 2012-10-24
Look at this article:

[https://help.ubuntu.com/community/HowToRemoveWindows](https://help.ubuntu.com/community/HowToRemoveWindows)

---

### Post by hozmaster on 2012-10-24
I don't want delete my windows partition, I want it used from virtalbox.

---

### Post by PowerBarry43 on 2012-10-24
Hi

As far as I know this isn't an easy thing to do. you can copy the partition then restore it back from inside virtualbox but you need to run sysprep on your windows vista first for that to work. I would recommend backing up anything you need from your Windows Vista partition to either your ubuntu partition or an external hard drive, delete the windows partition and expand your linux one to fill the gap then install Vista into a VM and restore your files that way.

Hope this helps!

Barry

---

