---
title: "Eliminate second boot option? How to?"
date: 2009-05-12
forum: General Help
---

### Post by rdmike on 2009-05-12
Hey all,

I have been trying Kubuntu and Ubuntu Studio in a dual-boot configuration for a little while now. Kubuntu I like but Ubuntu Studio, while loaded with great production software, has been an incredible disappointment.

Anyhoo, I'd like to get rid of it while keeping Kubuntu intact. I've been told I can simply delete the Ubuntu Studio partition(s) but how do I know which ones to delete. Also, how do I pull up a list of partitions? Thanks in advance!

---

### Post by bobnutfield on 2009-05-12
You can list your partitions with:

> sudo fdisk -l

but since they are both linux and both Ubuntu variants, you may not be able to immediately tell which is which.  The easiest thing to do is boot into the OS you want to keep and install Gparted, which is a GUI partition editor (you can get from the repos).  It is easy and intuitive.  Just open it and delete the partition you want to dispose of (which will be fairly easy since you cannot delete the partition you are running your current OS from, or a mounted partition.)

---

### Post by rdmike on 2009-05-13
Hi Bob,

Thanks for the reply, it was very helpful!

Now, I'm curious about another aspect of this issue. I was able to clear out, I think, the Ubuntu Studio partition and, in so doing, I set it to format as partition 3 thinking it would add to my existing partition but it doesn't seem to have worked as I now have two ext3 partitions. Did I goof?

---

### Post by michy99 on 2009-05-13
If you want it to be all one partition, delete the extra partition and then grow the current partition. You cannot do the second part while the partition is mounted so you have to do it from a Live CD, either an Ubuntu Live CD or Gparted Live CD.

---

### Post by rdmike on 2009-05-13
Ok, I did goof.

I just rebooted a short while ago and when I did I could not get the OS to load. It said "grub error 15."

I'm using the live disk now but how do I fix the issue? Help please!

---

### Post by Brandon Williams on 2009-05-14
It sounds like grub on your MBR may be configured to look for the stage2 bootloader on the partition that used to have ubuntu studio on it. Try reinstalling grub to the MBR.

First, figure out which partition has kubuntu on it, lets just say that it is /dev/sda3.
```
$ sudo grub
grub> root hd(0,2)
grub> setup hd(0)
grub> quit
$ 
```
The root command at the grub prompt tells grub that the stage2 bootloader is on /dev/sda3. You will need different numbers if kubuntu isn't on /dev/sda3. The setup command tells grub to install the stage1 bootloader to the MBR on /dev/sda.

There are plenty of howtos that go into more detail about how this works if my very brief summary isn't enough.

---

### Post by rdmike on 2009-05-14
Got it; thank you very much!

---

