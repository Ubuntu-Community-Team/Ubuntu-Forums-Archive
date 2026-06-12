---
title: "building a Live CD with a custom kernel?"
date: 2008-06-18
forum: Development CD/DVD Image Testing
---

### Post by gradedcheese on 2008-06-18
Hi.  I'm trying to put together a Live CD based on 8.04 but with my own 2.6.26 kernel that I built from source.  My CD boots but drops to a busybox shell and I am not sure why.  What is required to have a kernel that works with the 'casper' setup on the CD?

The guide here:
[https://help.ubuntu.com/community/LiveCDCustomizationFromScratch](https://help.ubuntu.com/community/LiveCDCustomizationFromScratch)
mentions using a "kernel and an initrd that was build with the casper scripts" ...how does one do that?

Thanks!

---

### Post by gradedcheese on 2008-06-19
Ok, I've now learned about squashfs and the fact that it gets loop mounted, which makes sense.  So the custom kernel needs to have squashfs support added as well as the loop block device enabled.

---

### Post by Nekosudachi on 2008-07-16
If you get your custom ubuntu 8.04 made would it be possible you could upload it somewhere as a torrent or open a ftp site?

I  upgraded my system and it won't pickup the sata controller on my geforce 8200 motherboard from ecs, And I hate to have to keep the old IDE hard drive for linux.
Thanks!

---

### Post by gradedcheese on 2008-07-16
Making a custom kernel for 8.04 is really easy, the trouble here was making one that will boot the Live CD.  If you want one for just normal (not Live CD) use, I can show you how to do it.  Otherwise I can upload the one I used for the Live CD, it has some issues but generally seems to work fine.

---

### Post by jett on 2008-09-11
> **gradedcheese said:**
> Making a custom kernel for 8.04 is really easy, the trouble here was making one that will boot the Live CD.  If you want one for just normal (not Live CD) use, I can show you how to do it.  Otherwise I can upload the one I used for the Live CD, it has some issues but generally seems to work fine.

care to share that image you have that can be used in a Live CD? I am trying to see if 2.6.26 will allow me to install Ubuntu on my P45-based motherboard (it uses the ICH10 chipset which I believe is not supported in the stock Hardy kernel).

or, 

it would be great if it isn't asking too much :) - it would be great if you can post instructions on how to do this. I am able to build a custom kernel using the instructions in the Ubuntu wiki. I am also able to create a LiveCD following instructions from the wiki. However, when testing it under qemu, it stops at the BusyBox prompt.

---

### Post by alain57 on 2008-12-31
hi i'm having the same problem
i made a custom iso of my system with remastersys
then i had the idea to compile my own kernel
i downloaded the lasted git ubuntu source (to have all included patches)

i setup the kernel with no module (all i need is compiled in the kernel)

of course i did not forget initrd, loopback, squashfs, unionfs

but when i boot (from cd, on hardrive my kernel works) i allways only go to busybox.
the casper.log end with an error mounting root any idea ?

---

### Post by newbee70 on 2009-01-12
> **alain57 said:**
> hi i'm having the same problem
i made a custom iso of my system with remastersys
then i had the idea to compile my own kernel
i downloaded the lasted git ubuntu source (to have all included patches)

i setup the kernel with no module (all i need is compiled in the kernel)

of course i did not forget initrd, loopback, squashfs, unionfs

but when i boot (from cd, on hardrive my kernel works) i allways only go to busybox.
the casper.log end with an error mounting root any idea ?

Did you do the update?


The only thing we need to do after installing casper is running **update-initramfs **to create an initramfs suitable for live CD/DVD.

---

