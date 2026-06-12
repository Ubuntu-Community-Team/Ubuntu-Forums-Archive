---
title: "VirtualBox Question."
date: 2009-05-16
forum: General Help
---

### Post by Roasted on 2009-05-16
I already set up Windows XP and I'm currently settings up Windows 7 in VirtualBox. I set them both up to be dynamically expanding, however each instance asked me to set a hard drive size. I set 10gb for XP. Does that mean if XP requires 12 gig cause of the stuff I put on it that it'll automatically resize to allocate that space?

If one night I get a virus on XP and I let it run and it decides to duplicate bogus folders so much to max out my hard drive, does that mean the 10gb partition could potentially max out my drive?

---

### Post by Legace on 2009-05-16
> **Roasted said:**
> Does that mean if XP requires 12 gig cause of the stuff I put on it that it'll automatically resize to allocate that space?

Yeah, it should expand automatically if it requires more space.
And yes, it probably could potentially max out your drive, but you can always delete the VDI (virtualbox image) from terminal if that happens :)

---

### Post by Roasted on 2009-05-17
What's the point of setting the drive space to be 10gb if it has the potential to max it out? Do you get a notification of some sort if that happens?

---

### Post by JKyleOKC on 2009-05-17
If you set the drive size to 10 GB, that's the maximum it will grow to. If you try to store 11 GB, you'll get a "disk full" error at 10. At least that's my understanding of it. My Vbox installations do not take nearly as much space as I've set them up to be, since I've not filled any of them up.

---

### Post by Roasted on 2009-05-17
Ahh, that makes more sense then. Thanks for that.

I'm really getting into this virtualizing. I'm actually going to set up Windows ME in a VM just to remind myself of the vicious past I've had prior to Ubuntu gracing me with its existence. :)

---

### Post by JKyleOKC on 2009-05-18
I'm running Vbox on two boxes here, and VMWare Server on another. The VBox installations are the Sun version, not the OSE one that's in the repositories; I added Sun's repository to my Software Sources lists and then installed via Synaptic. The VMWare Server is the latest version 2 and runs 24/7 to host my Email client in a WinXP VM. It's been running since last November 8 with only minimal downtime (rebooting after security updates) and even survived a power failure that exhausted its UPS. The VBox installations haven't had nearly so much of a workout but do seem quite robust also. One of them had VMs for Linux Mint and Puppy Linux; both of these were very slow -- but that box has only 256 MB of RAM to start with. It's now running a Win2K VM to do some maintenance of an obsolete software package, and that's doing okay even with such low RAM availability...

---

### Post by Mirge on 2009-05-18
> **Roasted said:**
> Ahh, that makes more sense then. Thanks for that.

I'm really getting into this virtualizing. I'm actually going to set up Windows ME in a VM just to remind myself of the vicious past I've had prior to Ubuntu gracing me with its existence. :)

Windows ME? *shudder*

---

### Post by adrianx on 2009-05-18
There are two options. This is how it is explained in VirtualBox help:
> 
 
[LIST]
[*]If you create a fixed-size image of e.g. 10 GB, an image file of roughly the same size will be created on your host system. Note that the creation of a fixed-size image can take a long time depending on the size of the image and the write performance of your hard disk.
[/LIST]

[LIST]
[*]For more flexible storage management, use a dynamically expanding image. This will initially be very small and not occupy any space for unused virtual disk sectors, but the image file will grow every time a disk sector is written to for the first time. While this format takes less space initially, the fact that VirtualBox needs to constantly expand the image file consumes additional computing resources, so until the disk has fully expanded, write operations are slower than with fixed size disks. However, after a dynamic disk has fully expanded, the performance penalty for read and write operations is negligible.
[/LIST]


---

### Post by albinootje on 2009-05-18
> **Roasted said:**
> I already set up Windows XP and I'm currently settings up Windows 7 in VirtualBox. I set them both up to be dynamically expanding, however each instance asked me to set a hard drive size.

Two big advantages of the dynamically creation are :
1) Very fast to create it (Try creating a static 10 Gb vdi instead)
2) It'll take only the space it is actually using in the vdi.

Let's assume that your XP installation in VirtualBox takes 1 Gb of disk space (No idea whether that's valid, but let's assume it for the sake of this example). Then you only have to make a backup of a 1 Gb vdi file for the initial install instead of the full 10 Gb.

---

