---
title: "GParted/Disk Utility Discrepancy"
date: 2011-10-13
forum: Desktop Environments
---

### Post by lotuseclat79 on 2011-10-13
I have a WD Elements 1T external hard drive which came formatted as a 1TB HPFS/NTFS (0x07) partition type according to Disk Utility, in addition to having an MBR.

I have resized the Volume partition to 80 GB with GParted 0.6.2 in an Ubuntu 10.10 (Maverick) Live CD environment.  Disk Utility 2.30.1 says the partition is 86 GB with 914 GB free.

Why does Disk Utility resolve to 86 GB and GParted 80 GB?

What accounts for this discrepancy?  Is this a software bug - in which software?

---

### Post by coffeecat on 2011-10-13
No discrepancy. If you look closely you'll see that Gparted reports in gibibytes (GiB), not gigabytes. Disk Utility reports in base 10 gigabytes (GB).

[http://en.wikipedia.org/wiki/Gigabyte](http://en.wikipedia.org/wiki/Gigabyte)

[http://en.wikipedia.org/wiki/Gibibyte](http://en.wikipedia.org/wiki/Gibibyte)

If you do the sums you'll see that 86GB = 80GiB (corrected to two places).

---

### Post by lotuseclat79 on 2011-10-14
> **coffeecat said:**
> No discrepancy. If you look closely you'll see that Gparted reports in gibibytes (GiB), not gigabytes. Disk Utility reports in base 10 gigabytes (GB).

[http://en.wikipedia.org/wiki/Gigabyte](http://en.wikipedia.org/wiki/Gigabyte)

[http://en.wikipedia.org/wiki/Gibibyte](http://en.wikipedia.org/wiki/Gibibyte)

If you do the sums you'll see that 86GB = 80GiB (corrected to two places).
Thanks coffeecat!

To make matters worse, fdisk -l reports in an unknown unit between GiB and GB, but calls it GB.

Talk about confusion - apparently, the NIST standard (10 August 2007) still needs to be standardized across commands in Linux distributions.

---

### Post by coffeecat on 2011-10-14
> **lotuseclat79 said:**
> Talk about confusion

Don't get me started! :)

Actually fdisk -l reports in cylinders, which is about as much use as a chocolate teapot. Or rather, the version of fdisk that came in Natty and before does. The Oneiric version of fdisk reports in sectors (which is much more useful) when you run fdisk -l for which you had to do fdisk -lu in earlier versions.

Talk about confusion!

There are those who, because kilo, mega and giga have traditionally been used to describe base-2 units in the early computing world, consider that they have a divine right to confuse the rest of the SI-prefix using world. I'm a pragmatist. I use giga (etc) for base-10 and gibi for base-2. Except when referring to a 2GB (2147483648 byte) RAM stick. 

Talk about confusion! :lol:

---

