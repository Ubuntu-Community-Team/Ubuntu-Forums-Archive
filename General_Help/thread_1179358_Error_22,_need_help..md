---
title: "Error 22, need help."
date: 2009-06-05
forum: General Help
---

### Post by Trygg on 2009-06-05
Okay, I made a partition on my Hard Drive, installed Ubuntu on it, and after some complications with my family (it's a family computer) about starting up, I erased the information on the partition and combined it back into my C: drive and now I get the Error 22 every time I try to boot without the Ubuntu disc I burned.

Extra stuff: I don't have my copy of Vista on a disc, it's on a partition of the C: drive, it was like that when I bought the computer.

---

### Post by whoop on 2009-06-05
So you got/want a machine with just windows on it and you get a grub error now?
If that's the case you need a windows cd to fix the mbr.

---

### Post by Trygg on 2009-06-05
So I need to go buy windows to get my computer back to normal? Even though I bought it with my computer?

---

### Post by Altay_H on 2009-06-05
> **Trygg said:**
> So I need to go buy windows to get my computer back to normal? Even though I bought it with my computer?
Nope. Just burn a copy of SuperGrub to a disk, then boot from it: [http://www.supergrubdisk.org/index.php?pid=5](http://www.supergrubdisk.org/index.php?pid=5)

It should give you the option to restore the MBR, fixing Windows. No need for the Windows disk.



EDIT:
If you still have your Ubuntu CD and don't feel like burning another disk, do what the post below mine suggests.

---

### Post by michy99 on 2009-06-05
Never mind.

---

### Post by whoop on 2009-06-05
> **michy99 said:**
> Try this:

```
http://www.arsgeek.com/2008/01/15/how-to-fix-your-windows-mbr-with-an-ubuntu-livecd/
```

That's cool...

---

