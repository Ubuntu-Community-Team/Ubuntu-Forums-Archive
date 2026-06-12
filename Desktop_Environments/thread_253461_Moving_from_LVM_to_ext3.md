---
title: "Moving from LVM to ext3"
date: 2006-09-08
forum: Desktop Environments
---

### Post by boomstik on 2006-09-08
I am trying to move a complete install of Ubuntu from an LVM volume group to a regular ext3 partition on the same drive.

here's a layout of my drive:

/dev/hda1 = /boot
/dev/hda2 = / (NEW Ubuntu root)
/dev/hda3 = lvm
/dev/mapper/Ubuntu-Ubuntu = / (OLD Ubuntu root inside LVM)

plus another unrelated FAT32 partition and the standard swap partitions, etc.

What I've done so far is:

1) boot from CD into rescue mode
2) create the ext3 filesystem on /dev/hda2
3) copy all data from /dev/mapper/Ubuntu-Ubuntu into /dev/hda2 (using the installer's partition editor). All data copied fine, i mounted /dev/hda2 and checked.
4) adjust GRUB - edited menu.lst to point to /dev/hda2
5) mounted /dev/hda2, edited fstab accordingly (replaced /mapper/Ubuntu-Ubuntu with /hda2)

6) Rebooted the system. it booted fine, but was still using the LVM volume as its root. We can't have that, can we? ;)
7) Created a Ghost image of the whole LVM partition. 
8) deleted the whole LVM partition

9) rebooted the system. After "booting the kernel:", received "Kernel panic: error reading memory image"

10) ??????

So right now, I have a /boot partition from which GRUB seems to attempt booting my system, and I have an ext3 partition containing the actual / of my Ubuntu. But then, why the kernel panic???

The scary part is that when I restore the Ghost image, I still receive the same Kernel panic. But I can mount any of the partitions and the data seems just fine...... ](*,) 

Any help, please???? I've searched everywhere, and it seems like something really small that I'm completely missing.....

---

### Post by tuxinvader on 2006-09-08
At the gurb prompt if you edit (e) the kernel entry you want to boot. What does the boot line say? Does it say "root=/dev/hda2"? 

Did you update /boot/grub/device.map?

---

### Post by boomstik on 2006-09-08
that's right - I changed it to say /dev/hda2

/boot/grub/device.map :confused: 

I don't remember updating it (can't check right now, I'm at work), but I would remember if I did that.

does that also contain links to the LVM which I should change to point to /dev/hda2?

---

### Post by tuxinvader on 2006-09-08
Yes, it maps system device names to grub device names

eg "/dev/sda1 (HD0,0)"

---

### Post by boomstik on 2006-09-08
Ah!! thanks, I'll check as soon as I get home.

---

### Post by boomstik on 2006-09-08
well, I checked device.map, and all it had was this:

```

hd(0) /dev/hda

```

I added the following:

```
hd(0,0) /dev/hda1
hd(0,1) /dev/hda2
```

which didn't help at all... the exact message I'm getting is:

```

Decompressing Linux...done.
Booting the kernel.
31.753513 Kernel panic - not syncing: I/O error reading memory image

```

and that's about it...

I don't understand... all the files normally needed to boot are right there.... :confused:

---

### Post by boomstik on 2006-09-08
okay, I fixed it!!!!! (with the help of [this thread]("http://www.ubuntuforums.org/archive/index.php/t-27371.html")).

Basically, what I did was to add "resume=/dev/hda5" to my GRUB menu.lst kernel line. /dev/hda5 is my swap partition.

it boots just fine from /dev/hda2, so I'll just leave it at that for now. My next step is figuring out how to tell initrd to use /dev/hda5 for boot, so that I don't have to use "resume" in menu.lst

---

