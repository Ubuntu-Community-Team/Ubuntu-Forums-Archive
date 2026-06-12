---
title: "SATA hotplug / hotswap support"
date: 2006-08-07
forum: Desktop Environments
---

### Post by folkfook on 2006-08-07
I have an Intel ICH7R chipset motherboard but it seems that the latest kernel of ubuntu(2.6.15-26) does not detect a sata drive after plugged in.
I am sure that the hard drive hot plug function does work in M$ windows.

Does Dapper 6.06 support hotplug feature?

---

### Post by Whoopie on 2006-08-07
Hi,

I don't think so. I made my own kernel with the hotswap patches from [http://home-tj.org/wiki/index.php/Libata-tj-stable](http://home-tj.org/wiki/index.php/Libata-tj-stable).

I then followed the howto on thinkwiki.org ([http://www.thinkwiki.org/wiki/How_to_hotswap_UltraBay_devices)](http://www.thinkwiki.org/wiki/How_to_hotswap_UltraBay_devices)).

But I have an ICH6 chipset.

Best regards,
Whoopie

---

### Post by thor918 on 2007-01-29
so hotplug works?

I have a promise tx4 and I can't seem to be able to detect hardware change in the bus without having to restart machine.
I want hotplug functionality!!
according to [http://linux-ata.org/driver-status.html#tx2](http://linux-ata.org/driver-status.html#tx2)
my card drivers supports hotplug. now how do I use that.
on the top of the page it reads : "This status report applies to the latest SATA driver release, found in kernels >= 2.6.18-git5 (i.e. what will be 2.6.19)."
so will that mean that I don't have to pach anything if I use kernel 2.6.19?

---

