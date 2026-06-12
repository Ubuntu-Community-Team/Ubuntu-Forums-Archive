---
title: "debootstrap, partitions"
date: 2009-01-23
forum: General Help
---

### Post by Gorlist on 2009-01-23
Afternoon, last few days ive been reading up on installing Ubuntu remotely via SSH. Nearly all topics ive found point to using debootstrap, and since then ive become slightly confused on how it works?

From what I understand you start by creating a partition on your hard drive, then from your existing Linux distribution run debootstrap which will manually download ubuntu files and extra into the correct locations on the new partition. 

After this you chroot and mount the new partition with your shiny new minimal install is located, and do a full update, including installing & setting up Grub.

Afterwards you then boot and hopefully after making sure Grub is pointing in the correct location it should load you new clean Ubuntu install? 

What happens to you previous partitions with the old distribution on? do delete it, then expand the new Ubuntu one to adsorb the free space?

Im also running software Raid 1, will this mirror any partition adjustments or is it going to be a pain to re-setup?

Theirs a guide ive come across over at serverbeach ([http://sbmonkey.wordpress.com/2008/06/25/ubuntu-on-serverbeach-a-step-by-step-guide/](http://sbmonkey.wordpress.com/2008/06/25/ubuntu-on-serverbeach-a-step-by-step-guide/)), now from how it reads they seem to have simply just reformatted their whole primary hard drive whilst its in use, now surely that wouldn't work? 

Best Regards,

---

