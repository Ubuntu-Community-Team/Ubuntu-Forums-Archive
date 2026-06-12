---
title: "ReInstalling/Upgrading"
date: 2008-12-28
forum: General Help
---

### Post by loudog23 on 2008-12-28
I currently run Xubuntu 8.04, i got into linux about 2-3 months ago.
So here i am, wanting to "renew" my linux (now i know what i want/don't want and how to set it up propely for my use)

30gb WinXp (htfs) on dual boot
50gb Xubuntu / (ext3)
swap partition
200gb /Home ext3

So, i want to freshly install Ubuntu (instead of Xubuntu) how can i?

1. install it over my current xubuntu partition WITHOUT keeping any setting and/or appication (i want it fresh)

2. keep all my personnal file on the /home partition and use this partition as /home with the new instalation (need to stay intact)

3. not screw up my dual boot (at worst i will re-GRUB once again :P )

i've search the forum without result, thanx in adavance
Louis

---

### Post by dcstar on 2008-12-28
> **loudog23 said:**
> I currently run Xubuntu 8.04, i got into linux about 2-3 months ago.
So here i am, wanting to "renew" my linux (now i know what i want/don't want and how to set it up propely for my use)

30gb WinXp (htfs) on dual boot
50gb Xubuntu / (ext3)
swap partition
200gb /Home ext3

So, i want to freshly install Ubuntu (instead of Xubuntu) how can i?

1. install it over my current xubuntu partition WITHOUT keeping any setting and/or appication (i want it fresh)

2. keep all my personnal file on the /home partition and use this partition as /home with the new instalation (need to stay intact)

3. not screw up my dual boot (at worst i will re-GRUB once again :P )

i've search the forum without result, thanx in adavance
Louis

You should be able to shrink the existing Xubuntu partition to make more room for another install (~10-12GB required). You may have to delete the existing swap partition and put any new partitions in an Extended partition.

If you install over an existing partition then those applications in the existing will be wiped. Your /home partition will keep all the configuration that you already have and any new install will use it.

There are numerous posts in the forums on resizing and creating partitions.

---

### Post by loudog23 on 2008-12-28
> **dcstar said:**
> You should be able to shrink the existing Xubuntu partition to make more room for another install (~10-12GB required). You may have to delete the existing swap partition and put any new partitions in an Extended partition.

can i just delete old xubuntu + swap, recreate and install?

> **dcstar said:**
> If you install over an existing partition then those applications in the existing will be wiped. Your /home partition will keep all the configuration that you already have and any new install will use it.


Thanks, that's exactely what i wanted to know.

---

