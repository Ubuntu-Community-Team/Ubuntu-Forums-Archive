---
title: "how fast should md resync actually be?"
date: 2009-04-26
forum: Desktop Environments
---

### Post by mdurkin on 2009-04-26
Hi All,
I have Ubuntu 9.04 with 4x1TB drives arranged in a raid 5 array, with lvm and ext4 on top.
I've been having a few problems with loosing power, so the array has rebuilt a couple of times.
I was wondering what the experience of others is regarding resync speed. Mine seems to be taking a long time, with not huge amounts of disk activity or cpu use (25% on one core).
I'm getting speeds of 25482K/sec. I have adjusted the min and max speeds but it doesn't seem to make much of a difference:
proc/sys/dev/raid/speed_limit_max 600000
/proc/sys/dev/raid/speed_limit_min 300000

My hardware is an Atom 330 based board, with an add-on PCI - Sil3114 based sata controller. Perhaps this is the PCI bus limiting the rysnc?

thoughts appreciated. Maybe I need to look out for one of those new nvidia ION boards :o)
Matt

---

