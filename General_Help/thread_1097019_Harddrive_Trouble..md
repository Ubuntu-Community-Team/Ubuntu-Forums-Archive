---
title: "Harddrive Trouble."
date: 2009-03-15
forum: General Help
---

### Post by Reeman on 2009-03-15
The computer that I built for my brother is starting to have a harddrive failure. Just wondering if it is easy to dd a complete install to save a good setup?

For one I see that the etc/fstab is based on uuid data not just good old permissions... so how does this effect putting it on a different drive? Will it barf on the different size partition tables created on a different drive?

The way that I set him up was with a different /home on a primary partition, and root on the first. It is partitioned with three primaries one for root which is about 30 gig one for swap which is 2 gig and the rest of the 200 gig which is /home. 

This is the way I always set things up because 99% of what he records (audio) is saved in /home. We both do home hd audio recording.

In theory I should be able to just use a knoppix cd and dd his failing drive partition contents to a second drive with the same three primary partition setup. Swap out the drives then boot to the new drive with an Ubuntu cd and fix grub. That way the required drive partition letters will be identical, and there should be no problems unless Ubuntu needs to have the uuid data changed...which could be almost impossible.

Anyone see any trouble doing the deed?

---

