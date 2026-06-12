---
title: "iPhone in partition table"
date: 2011-01-10
forum: Desktop Environments
---

### Post by Teuntjuuh24 on 2011-01-10
Hi guys,

I've got an iPhone that i want to see in the partition table of ubuntu 10.10.
Now i know that my phone is mounted on my system, i can play songs from it etc..
But my main objective is to create a digital copy of the phone for forensic investigation and i was hoping to do that by creating a digital copy with dd or dcfldd. 
As far as i know, i can only create a copy if i know the mountpoint. The mountpoint is shown in properties and it says: /inode/directory/.

I installed the idevice library's and i dont get any errors anymore.
Can anyone help me getting the iPhone in the partiton table? Or creating a copy of it?

thanks in advance!

---

### Post by Joe of loath on 2011-01-10
What do you mean 'get it into the partition table'?

What's the output of fdisk -l?

---

### Post by mrkazoodle on 2011-01-10
run palimpsest
(or 'system' > 'admin' > something like 'disk utilities' (I have a translated version so I don't know it's English name))

---

### Post by Teuntjuuh24 on 2011-01-11
> **Joe of loath said:**
> What do you mean 'get it into the partition table'?

What's the output of fdisk -l?

it only gives like /dev/sda1 sda2 sda3 etc. Normally i would get /dev/sdb1 just like a normal usb device.

---

