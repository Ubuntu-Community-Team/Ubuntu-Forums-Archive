---
title: "ubuntu boot loader"
date: 2006-01-10
forum: Desktop Environments
---

### Post by mattwestm on 2006-01-10
Ok, I just installed Ubuntu on another partition. I am using the Fedora Core Grub  boot loader. Ubuntu is on partition hdb1 and swap is hdb2. What do I need to put into the grub.conf file to be able to boot Ubuntu properly? Thanks in advance, Matt-

---

### Post by jerrykenny on 2006-01-10
Matt, I reckon you should chainload for the following reason

When you update a kernel using synaptic,   you'll be able to select from your old /new kernels without any further interaction . . . .

to do that . . . .try

(in Ubuntu)

sudo grub-install hd1


hd1  being equivalent to hdb, then edit your Fedora grub.conf & add this


title		Ubuntu
root		(hd1,0)
chainloader	+1
boot

---

### Post by mattwestm on 2006-01-10
Ok, here's the thing. I can't even boot Ubuntu. When I tried the method listed previously, I get:

root (hd1,0)
Filesystem type is ext2fs, partition type 0x83
chainloader +1

Error: 13 Invalid or unsupported executable format

I just need to add the correct kernel number and image into the Fedora grub.conf file. And, that I don't know. And, I have never been able to boot it, so, there are no upgrades on it or anything. Just default CD settings.

Thanks in advance, Matt-

---

