---
title: "Partition Virtual Drive before Installing Operatin Systems"
date: 2010-08-13
forum: Desktop Environments
---

### Post by jhmaccuish on 2010-08-13
Hello,

I have an acer laptop (TravelMate 7320) which came with Windows Vista. I have made copies of the recovery disk for vista and installed Ubuntu 10.04 and would like to run Vista from a virtual machine in Ubuntu and for this purpose I installed Virtualbox. The problem is that the recover disk that acer provide require the hard drive to partitioned  in a certain way otherwise the installation process error outputting "No partition available".

Acer do provide a bootable CD for download from there website to partition the drive before installing from their recovery disk but I have tried this with virtual box and the process doesn't detect the virtual drive. So my question is does anyone know of a virtualisation software for Ubuntu that they could recommend that allow for the partitioning of virtual disk before the installation of an OS? Or even better does anyone know how to do this with Virtualbox?

Thanks,

Jamie.

---

### Post by aeiah on 2010-08-13
you should be able to partition it with a gparted livecd quite easily. the reason that acer disk doesnt work may be because it looks for an acer motherboard or something. obviously, it sees a virtualbox motherboard, and so decides not to run. either that or it checks something else like a hdd id number or something.

either way, i guess you'll have to use gparted. you'll probably find that the recovery disk and whatnot also check that its being installed to an acer system, and so they won't install for you either. if you download vista from somewhere else and try and use your acer windows key, you may find that it also doesn't work because your key is tied to the acer manufacuterer version of vista!

gotta love windows. you can try and it may work, but you may find it easily to aquire a version of vista by other means rather than use your legal copy.

---

### Post by gadolinio on 2010-08-13
Yes, you can partition the virtual hard disk with gparted. In the virtual machine's configuration, in virtualbox, choose to boot from CD first, and use a liveCD in your CD drive; you can alternatively use a disk image of ubuntu (ubuntu-blah-blah-blah.iso) to boot the virtual machine. Either way, once in the liveCD's session open system--administration--gparted partition editor, and set the partitions as needed.
Hope you find this useful...

---

