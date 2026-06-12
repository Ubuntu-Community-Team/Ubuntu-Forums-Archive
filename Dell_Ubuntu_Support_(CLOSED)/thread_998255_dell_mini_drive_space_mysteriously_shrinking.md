---
title: "dell mini drive space mysteriously shrinking"
date: 2008-11-30
forum: Dell Ubuntu Support (CLOSED)
---

### Post by milton1 on 2008-11-30
For some reason the hd space on my mini 9 is slowly shrinking. Almost every time I run the machine, my drive space seems to shrink by a few MB. This happens even if I add nothing new to the system, run no updates, etc. Now, I have made an attempt to upgrade to 8.10, but before I committed any changes, the partitioner crashed, so I canceled and rebooted just fine to the 8.04 system it shipped with, only to discover that the disk was down 30 MB! What gives? Is this maybe the system attempting to write to the disk somehow to deal with too little RAM? I do have only the basic 512 MB RAM installed. I am awaiting the arrival of a 2 GB RAM stick (Major reason to want to go to 8.10, need highmem support in the kernel). Any thoughts on where my disk space is going?

Spec:
Dell mini 9
ubuntu 8.04 dell custom install
4GB ssd
512 MB RAM

---

### Post by sdennie on 2008-12-02
> **milton1 said:**
> For some reason the hd space on my mini 9 is slowly shrinking. Almost every time I run the machine, my drive space seems to shrink by a few MB. This happens even if I add nothing new to the system, run no updates, etc. Now, I have made an attempt to upgrade to 8.10, but before I committed any changes, the partitioner crashed, so I canceled and rebooted just fine to the 8.04 system it shipped with, only to discover that the disk was down 30 MB! What gives? Is this maybe the system attempting to write to the disk somehow to deal with too little RAM? I do have only the basic 512 MB RAM installed.  Any thoughts on where my disk space is going?

Spec:
Dell mini 9
ubuntu 8.04 dell custom install
4GB ssd
512 MB RAM

Log files can take up room.  Also, things like Firefox, and various other apps that create caches on disk will cause the same sort of behavior until they reach their maximum cache size.

> 
I am awaiting the arrival of a 2 GB RAM stick (Major reason to want to go to 8.10, need highmem support in the kernel).


I'm not sure what you mean here.  The 32-bit versions of both Ubuntu 8.04 and Ubuntu 8.10 support up to around 3.5GB of RAM (HIGHMEM4G) in the default kernel.  Neither have -generic kernels compiled with HIGHMEM64G (which allows for up to 64G of RAM).

---

### Post by zenarcher on 2008-12-02
I think what he means, in respect to RAM, is that the Mini 9, as delivered by Dell, with Ubuntu 8.04, is only able to see 1GB of RAM.  Dell does not offer any option above 1GB and the kernel, as used by Dell, will not recognize more than 1GB.

One can install a 2GB stick of RAM and if you install the standard Ubuntu 8.04 or 8.10, you then see and can use the 2GB.  It's something Dell has done to cripple the RAM capability, apparently due to their offering Windows XP and a requirement of MS, in order to offer XP on the netbooks.

Cheers,
zenarcher

---

### Post by sdennie on 2008-12-02
Ahhh.  I wasn't aware they'd done that.  If it's just at the kernel level, you can probably avoid doing a complete re-install and try:

```

sudo apt-get install linux-generic linux-imagine-generic linux-headers-generic linux-restricted-modules-generic linux-ubuntu-modules-generic

```

Then, reboot and in the grub menu, choose the linux generic image.

---

### Post by iggykoopa on 2008-12-02
They actually are using different repositories, he'll have to reinstall to get the full ram. I wish I knew what the benefits are of the kernel they are using though, it's the lpia kernel (low power intel architecture).

edit: he may be able to use the normal repos just to install the kernel but I don't think I'd recommend it.

---

### Post by sdennie on 2008-12-03
> **iggykoopa said:**
> They actually are using different repositories, he'll have to reinstall to get the full ram. I wish I knew what the benefits are of the kernel they are using though, it's the lpia kernel (low power intel architecture).
[/quote

Ahh.  That makes it more difficult.

[quote]
edit: he may be able to use the normal repos just to install the kernel but I don't think I'd recommend it.

That's what I was thinking at first too but, it sounds like it would be the equivalent of installing and AMD64 kernel on an x86 install.

---

