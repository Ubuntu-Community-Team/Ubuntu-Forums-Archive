---
title: "Installing Bootable ISO into Grub?"
date: 2009-01-04
forum: General Help
---

### Post by Kissell on 2009-01-04
Okay, I used the option in Intrepid to create a USB boot disk out of my phone...  awesome, now I can boot to Ubuntu anywhere, and I've got free space on the microSD card in my phone!!!

Now what I want to do, is be able to boot into many OS's...  have a portable hay day!!!  but the USB boot disk program only seems to work with my Ubuntu ISO image...  

I want to somehow install more OS's into Grub from the ISO images I have...  (or at least be able to install each of these ISO images to a separate USB stick).  

Currently I have many ISO images that I use, to create CDs, to boot into those CDs and do specialized tasks...  for instance I use "Darik's Boot and Nuke" a lot to wipe disks, or the "gParted Live CD", or "Nero BackItUp", and "System Rescue CD".  

Ideally I'd love to be able to install those ISO images into the grub boot loader, so that my Ubuntu portable OS USB stick can also be the USB stick to load any of those other programs I use...  or, what would also be nice, is a program similar to writing an ISO to a CD to make it bootable, but for USB...  the "Create USB Bootdisk" icon in Intrepid works great for creating a Ubuntu boot disk to a USB drive, but it doesn't seem to work for these other ISO images.

Plus, I would love to be able to install hardy and intrepid on the same USB stick, and get a choice of which to boot too, because Intrepid won't boot on many of my machines, hangs at initramfs screen.

---

### Post by pyromanic123boom on 2009-01-04
You have to create partitions inside the "hard drive" (flash card) and then install the operating systems to those partitions. Then you have to label them in the grub bootloader (/boot/grub/menu.lst). 

Basically you want to dual-boot operating systems from a flash card. Not the best idea - limited in space, etc., but if you still want to, you'd be best with searching google on how to create dual-boot systems. 

An external hard drive or large flash drive would be a better option than what you've got currently.

---

### Post by Kissell on 2009-01-04
Yeah, I'm going to use a 500gb 2.5" external laptop drive for mine... but my brother wants to use his phone, which can act as USB flash drive...  and that's fine, he has 16GB on his microSD card, which is plenty...

Out problem though, is not in partitioning the disk or anything like that... it's more of an issue of "how do you transfer a bootable CD or ISO image to that partition?"

Many of these bootable CDs came to us as ISO images...  I don't have like the OS installer program that would allow me to install them to a partition.

---

### Post by pyromanic123boom on 2009-01-05
Oh, ok. Well you'd need to put the card into a reader or something (access on the computer) and then you can extract the ISOs to the particular partitions. If there's multiple partitions on the card, different drives should come up in nautilus.

You can always download installer versions of most linux distros as well, if that makes it easier.

---

### Post by Kissell on 2009-01-05
Well, ideally we'd like to be able to boot the USB drive to a grub menu loader and have choices for which program to load up...  each one came to us as an ISO image, and no installer version is publically available.  

For instance, something like DBAN (Darik's Boot and Nuke), I can burn the ISO to a CD and boot to it, but I don't want to have to do that, i'd really like it if the program were already on my USB drive and I could just boot to it as one of the options.

Alternatively, getting them to run inside of Ubuntu would be even better, as then I wouldn't have to dual-boot, i already can boot to Ubuntu.  But many of these ISO images are bootable and boot into linux, but into a different type (non-debian linux) and there doesn't seem to be an easy way to make them work in Ubuntu...  originally there was no need for this, as the tools would often be working with what would have been your boot partition, but now that you can boot to a USB drive the tools can operate on the hard disks unimpeded, so now I have a need to have the tools loaded in Ubuntu, even though for 99% of the time you'd be booting Ubuntu from your hard disk and the tools would be useless, it'd still be nice to have them work in Ubuntu so that you could use them when booting to Ubuntu via a USB drive.

---

