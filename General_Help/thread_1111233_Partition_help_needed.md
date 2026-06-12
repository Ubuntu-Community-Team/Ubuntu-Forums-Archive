---
title: "Partition help needed"
date: 2009-03-30
forum: General Help
---

### Post by letmekilluplz on 2009-03-30
Ok I had Ubuntu installed on my portable hard drive (250GB). Now I have installed it on my computers hard drive(140GB) on a 70GB partition. (70 for Windows, 70 for Ubuntu)

Now the question is .. How do I delete the 25GB Ubuntu partition off of my protable hard drive and make them 1 partition?

P.S I have GParted installed.

P.S.S Sorry about my ramblings and sorry if this is a stupid question I am new to Lunix/Ubuntu.

---

### Post by kestrel1 on 2009-03-30
Open Gparted, select your external drive & then select the Ubuntu partition/s & delete them. Then resize the existing partion to incorporate the free space.

---

### Post by letmekilluplz on 2009-03-30
I will try it thanks!

---

### Post by letmekilluplz on 2009-03-30
It wont let me resize or move it:confused::(

---

### Post by kestrel1 on 2009-03-30
Have you tried deleting it first?

---

### Post by letmekilluplz on 2009-03-30
I deleted the Ubuntu partition but it says that it can't read the contents of this filesystem some actions may be disabled. I would guess thats whats wrong but I dont know how to fix it...

---

### Post by ibuclaw on 2009-03-30
Are all partitions on the External Hard Drive unmounted?

If you can see a small padlock next to one of the listed partitions on the disk, right-click and there should be an option for you to unmount it.

You won't be able to do any resizing/editing of partitions otherwise.

Regards
Iain

---

### Post by letmekilluplz on 2009-03-30
> **tinivole said:**
> Are all partitions on the External Hard Drive unmounted?

If you can see a small padlock next to one of the listed partitions on the disk, right-click and there should be an option for you to unmount it.

You won't be able to do any resizing/editing of partitions otherwise.

Regards
Iain

All the unmount options are grayed out and there are no padlocks.

---

### Post by kestrel1 on 2009-03-30
Are the external drives partitions showing on the desktop? If so, right click on them & select unmount.
You may want to boot from the Live CD & try the partition operation from there.

---

### Post by letmekilluplz on 2009-03-30
Hmmm well they weren't showing up on the desktop but it let me edit them through the live CD. Weird problem but problem solved thanks!

---

### Post by kestrel1 on 2009-03-30
There must have been something that was not dismounting the USB correctly & using the Live CD sorted that out.
Glad it worked for you.

---

