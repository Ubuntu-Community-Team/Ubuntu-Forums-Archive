---
title: "Windows directory share in a VM"
date: 2013-03-20
forum: Desktop Environments
---

### Post by Pyrophorus on 2013-03-20
I run Linux 12 through a VM (lousy UEFI), on a windows 8 laptop.

I would like to access a windows directory (already set to share on the windows side), through Ubuntu.
I don't want to move it, just access it, and use the files there.

---

### Post by albandy on 2013-03-21
sudo mount -t vboxsf your_share_name Destination_mountpoint

---

### Post by cortman on 2013-03-21
And if you want the folder to automatically mount when you start the VM, you can add a line to rc.local- I detail how to do that [here]("http://cortman.wordpress.com/2013/03/14/lubuntu-12-10-virtual-box-setup/").

---

### Post by Pyrophorus on 2013-03-22
I get
mount : unknown filesystem type 'vboxsf'

---

### Post by albandy on 2013-03-22
> **Pyrophorus said:**
> I get
mount : unknown filesystem type 'vboxsf'

have you installed guest additions?

---

### Post by Pyrophorus on 2013-03-22
> **albandy said:**
> have you installed guest additions?

You'll have to explain to me what that is, sorry?

---

### Post by cortman on 2013-03-23
You need to install the VirtualBox Guest Addtions- it's a bunch of kernel modules and other programs. If you take a look at the link I gave you in my previous post, it will explain how to install them.

---

