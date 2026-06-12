---
title: "extending a partition"
date: 2009-05-30
forum: General Help
---

### Post by yon2501 on 2009-05-30
ok so i have a dual boot laptop that i just got the way i want it, windows xp and ubuntu 9.04. thing is ive got the hard drive partitioned with just enough space to run both operating systems then the rest is linux-swap and a shared ntfs for storage unfortunately the windows partition needs to be extended by about 5 gigs and the shared taken down by 5, windows is sda1 ubuntu is sda2 linux-swap is sda3 and the shared is sda4, is there a way to extend sda 1 without having to reformat the entire drive?

---

### Post by Legace on 2009-05-30
You can resize easily with GParted.
If you don't have it installed, type in the following in Terminal:
```
sudo apt-get install gparted
```

To launch, simply type:
```
sudo gparted
```

;)

---

### Post by yon2501 on 2009-05-30
yeah ive got gparted but the problem is that i cant add the space i take off of the shared partition and add it to the windows partition because theres the linux swap and ubuntu partitions in between them

---

### Post by drs305 on 2009-05-30
My recommendation would be to move swap (swapoff first) to the far right of the free space and reduce it to no more than 2GB. Then move sda2 right. That should give you 9GB of space you can expand sda1 with (or split between it and sda2). Your swap really doesn't need to be 7GB.

Back up any important data before doing any repartitioning.

If you want to resize sda4, you would shrink sda4 first, then move swap, sda2, and expand sda1.

---

### Post by yon2501 on 2009-05-30
well how do i go about moving sda2 i dont have a live cd handy atm so i have to be booted into ubuntu sda2 to use gparted

---

### Post by drs305 on 2009-05-30
> **yon2501 said:**
> well how do i go about moving sda2 i dont have a live cd handy atm so i have to be booted into ubuntu sda2 to use gparted

You won't be able to do any partition work from within ubuntu. sda2 is the system partition and you can't work on sda2 as long as it is mounted. Gparted is on the gparted cd and the systemrescue cd, but you would have to create them as well if you didn't have one handy.

There is probably partitioning software you can run from within windows but I have no experience with them as far as linux partitions are concerned.

---

### Post by yon2501 on 2009-05-30
i have experience with them and the free ones are horrid, guess ill have to wait til my buddy gives me my live cd back. thanks for the advice

---

### Post by carml on 2009-05-30
Just download the Gparted LIve version from the official site or from an other,butn it to a cd and reboot with it in the optical drive.
Doing so you'll be able for sure to make all changes to the partitions without issues,because the Live of Gparted is a Gentoo mini distro thought to be used to manipulate the partitions.
Ne too I have one and used to resize Win%&^$ Vista partition :).

---

### Post by yon2501 on 2009-05-30
i would but i dont have any blank cds atm and id just do a live usb but ive misplaced my flashdrive, suposed to see the guy later today tho so who knows

---

