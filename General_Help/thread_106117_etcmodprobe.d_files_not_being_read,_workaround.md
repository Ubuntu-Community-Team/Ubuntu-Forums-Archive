---
title: "/etc/modprobe.d files not being read, workaround"
date: 2005-12-19
forum: General Help
---

### Post by tpoindex on 2005-12-19
I thought I'd share a modules (and /etc/modprobe.d) problem and my
workaround, I've seen a few posts with similar module problems.

I have an ASRock 939Dual-SATA2 motherboard with onboard ethernet, but
unfortunately the ULi implementation of the Tulip chip is slightly buggy.
The 'tulip' driver in 2.6.12 doesn't deal with the chip quite right in that 
the media table is not auto-detected correctly.  It turns out that manually
specifing the media type can resolve the problem for now (looks like more recent kernels have a fix for the ULi tulip chip).  I can get ethernet working with:

    modprobe -r tulip
    modprobe tulip options=0x0d

The 'options=0x0d' specifies "MII 100baseFx-FDX" media. ** 

According to 'man modprobe.conf', I should be able to add a file /etc/modprobe.d/tulip with one line:

    options tulip options=0x0d

but no matter what  I tried, I could never get the tulip options to be set
when the machine booted.  It seems that the tulip driver was being
loaded from the initrd.img that was build during install, and of 
course didn't see the files in /etc/modprobe.d/*.

I finally stumbled upon this workaround:  /etc/modules is a list of
modules to be loaded early in the boot process, so I added:

    -r tulip
    tulip options=0x0d

The first line removes the module that was previously loaded, the 
second loads the tulip driver again with the required option.  Now
my networking starts up at boot time. 

Hope this helps others.


** Other media types for the tulip driver, from tulip_core.c, starting
at index '0', e.g  0x0d == 12 ==  "MII 100baseTx-FDX"

        "10baseT", "10base2", "AUI", "100baseTx",
        "10baseT-FDX", "100baseTx-FDX", "100baseT4", "100baseFx",
        "100baseFx-FDX", "MII 10baseT", "MII 10baseT-FDX", "MII",
        "10baseT(forced)", "MII 100baseTx", "MII 100baseTx-FDX", 
        "MII 100baseT4",
        "MII 100baseFx-HDX", "MII 100baseFx-FDX", 
        "Home-PNA 1Mbps"

---

