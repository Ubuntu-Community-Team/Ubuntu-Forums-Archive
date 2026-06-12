---
title: "[lilo] Upgrading kernel"
date: 2005-06-12
forum: Desktop Environments
---

### Post by globe_trotter on 2005-06-12
Hi all,
i've a trouble with the installation of a new kernel image..
I simply downloaded 2.6.11.12, patched for the pwc webcam support,
make oldconfig with kubuntu's config ('couse in a hurry i erased my old config)...

Then configured the kernel (don't think there are mistake) builded it..
and putted the image and the System.map in /boot....

Configured lilo, after lilo && reboot got a freeze of the system..
It doesn't start at all loading the image... It should print some dots and then the kernel should bootstrap... but it dont.. simply

loading Linux.

and no more..
For information...
my config: [http://www.cs.unibo.it/~ecataldi/config-2.6.11.12](http://www.cs.unibo.it/~ecataldi/config-2.6.11.12)
my lilo: [http://www.cs.unibo.it/~ecataldi/lilo.conf](http://www.cs.unibo.it/~ecataldi/lilo.conf)

Thanks for the attention :)

EDIT: ahem.. maybe i forgot some information  :) 

A7v880+sempron
ide discs, gcc-3.5...
The freeze happens un the lilo's "bios data check",..

Really i can't understand.. Thanks in advance :)

---

### Post by iceman on 2005-06-14
I had the same problem in two different machines...
I don't like grub, and after installed kubuntu, i put lilo instead grub.
In both, i tried to install my own compiled (correctly) kernel, but after rebooted i only get hang up.
The strange thing is that if i use old System.map and old initrd.img, but i point to new kernel, it takes the old kernel!! (obviously, using dual kernel boot).
Seems like lilo have some bug...

---

### Post by !nkubus on 2005-06-14
I had the same error upgrading from Debian Unstable to kubuntu on my laptop :( so now it does not boot anymore and i don'T want to reformat again :( so is there a way to install grub with a boot cd so it will reconize my dual boot (it's my work laptop) so i don't want to erase my winXP partiton or my boss is gonna kill me ;).

---

