---
title: "Effect of installing lvm2?"
date: 2009-02-13
forum: General Help
---

### Post by lesliek on 2009-02-13
I'm running v 8.10.

A friend's computer gave up the ghost. She was running Fedora 9. She had two internal hard disks. They constituted a single volume group. (I hope I've got the terminology right.)

I'm trying to recover her data from the two hard disks. To that end, I've removed both hard disks from her computer and am able to connect both of them to mine via IDE-to-USB adapters.

I found a document on the Web entitled "Accessing a Fedora Logical Volume from Ubuntu".

It requires me to install lvm2 on my computer as a prelude to trying to mount the volume group composed of the two hard disks.

I don't know whether installing lvm2 on my computer may adversely affect my system in some way.

I'd be very grateful for guidance on that.

Thanks very much for reading this.

Leslie

---

### Post by bhaverkamp on 2009-02-13
Installing lvm2 should be safe. Just be careful to not accidentally add you existing disks to the volume as they would get reformatted. Tred lightly. If you can do all this from a VM so much the better.

---

### Post by lesliek on 2009-02-13
Thanks very much for your quick reply.

Here, in order, are all the instructions in the document (which assumes that the relevant volume group is VolGroup00 and the relevant logical volume is LogVol00):

$ sudo apt-get install lvm2
$ sudo modprobe dm-mod
$ sudo vgscan
$ sudo vgchange -ay VolGroup00
$ sudo lvs
$ sudo mkdir /mnt/fcroot
$ sudo mount /dev/VolGroup00/LogVol00 /mnt/fcroot -o ro,user

Unless the mere act of installing lvm2 starts a chain reaction of some type, none of those commands SEEMS to threaten adding my own hard disk to the volume group.

As to using a VM, this is already way above my head. I couldn't think of adding that issue to this one!

Thanks again,

Leslie

---

### Post by bhaverkamp on 2009-02-16
Yup, I agree. Did you try it?

---

### Post by lesliek on 2009-02-16
I've taken the coward's way out. When her computer gave up, I got another computer going for her on which I've also installed Ubuntu 8.10. As she hasn't built up any data on it yet, I'm going to try using lvm2 on THAT computer. If it works, great. If it doesn't AND it also causes problems with that computer, I just have to do a fresh install on that computer.

I'll try it on the weekend.

I really appreciate your being interested in this and helping.

Thanks,

Leslie

---

