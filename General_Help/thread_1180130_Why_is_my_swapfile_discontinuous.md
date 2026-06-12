---
title: "Why is my swapfile discontinuous?"
date: 2009-06-06
forum: General Help
---

### Post by Richardcavell on 2009-06-06
Hi.

I have an Ubuntu 9.04 64-bit installation on a 16 Gig partition.  It currently has 6 Gigs of free space.  I just upgraded my MacBook2,1 from 1 Gig to 3 Gig RAM.

Linux currently has no swapfile.  I'm trying to give it a swapfile, which I also want to use to be able to hibernate the machine.  (I have never done this successfully in Ubuntu by the way, though it works flawlessly in OS X).

To create a swapfile I did:

sudo dd if=/dev/zero of=/swapfile bs=1024 count=5200000

I now do:

sudo filefrag =v /swapfile

to find the first block number, and it gives me:

Discontinuity: Block 1170062 is at 1723040 (was 1722297)
Discontinuity: Block 1170075 is at 1723055 (was 1723052)
Discontinuity: Block 1170078 is at 1723088 (was 1723057)
Discontinuity: Block 1171413 is at 1724426 (was 1724423)

Now, it goes on for pages with this kind of thing, and then:

/swapfile: 1190 extents found, perfection would be 41 extents

What's going on?

Richard

---

### Post by Legace on 2009-06-06
Why don't you use GParted?
You'll need to make 3GB (or more) of free space, and create a swap partition there :)

---

### Post by 3Miro on 2009-06-06
Linux doesn't use a swap file. Linux uses swap partition. Use GParted to create a swap partition.

---

