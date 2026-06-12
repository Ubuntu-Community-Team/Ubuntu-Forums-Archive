---
title: "Resizing my Ubuntu EXT3 partition?"
date: 2009-06-01
forum: General Help
---

### Post by yonyz on 2009-06-01
Hi,

I got XP installed for a few months now, and yesterday I've installed Ubuntu 9.04 through the Live CD.
I selected the option to install it aside XP and choose the operating system to boot into when the computer starts.
So far, everythings works fine.

Now I want to extend my ext3 partition so I can install some basic software like Java 6. How can I do that while leaving it bootable?
Can I resize it through XP (Acronis Disk Director Suite) and then use GParted to mark it as the boot partition, or it's not that simple?

---

### Post by yonyz on 2009-06-01
Bump.

---

### Post by whoop on 2009-06-01
You need to do it from a livecd

---

### Post by MichaelSammels on 2009-06-01
Well, I would assume that if you use your parition software to resize your ext3 partiton towards the end of the disk, then maybe. I'm not too sure though. Perhaps you could shrink the XP Partition?

---

### Post by yonyz on 2009-06-01
The XP partition is already shrinked. I got 20GB of unpartitioned space.
What's next?

---

### Post by MichaelSammels on 2009-06-01
Using your parition software, move the ext3 partition so that the 20GB space is at the end of the disk, then extend. You are better to do this using an Ubuntu LiveCD and gparted (Partition Editor). This may cause filesystem damage, since I'm not too sure if GRUB will be happy with moving a partition. Any problems, and reversing it should be OK. Let us know if it works. :)

---

### Post by Legace on 2009-06-01
> **yonyz said:**
> The XP partition is already shrinked. I got 20GB of unpartitioned space.
What's next?

Post a screenshot of GParted, and I'll tell you what you should do to avoid problems.

---

### Post by yonyz on 2009-06-01
MichaelSammels: How do I move a partition to a specific place in the disk?
Legace: How am I gonna get a screenshot inside GParted?

---

### Post by MichaelSammels on 2009-06-01
Press the Prt Scr key at the top right of your keyboard, and upload it here.

---

### Post by yonyz on 2009-06-01
I know how to take a screenshot. But where am I gonna save it when I'm inside GParted?
We're talking about the GParted boot disc, aren't we?

---

### Post by Legace on 2009-06-01
> **yonyz said:**
> I know how to take a screenshot. But where am I gonna save it when I'm inside GParted?
We're talking about the GParted boot disc, aren't we?

No. Open Ubuntu.
Then type the following into Terminal:

```
sudo apt-get install gparted
```

Once you've installed it (or if you already have it), type in the following to open GParted. Then take a screenshot (it will save to Desktop as default) and post here:
```
gksudo gparted
```

---

### Post by yonyz on 2009-06-01
Great, now I can't even boot into Ubuntu because there is no disk space available for the graphic environment.
Can I fix the partitioning issue through Windows?
If the answer is yes, please tell me how to do it.
If not, I don't mind formatting Ubuntu and reinstalling it in the proper way that will let me resize it's partition when necessary.

---

### Post by yonyz on 2009-06-01
My brother did a clean new install for me. Everything works fine now.
Thank you all.

---

