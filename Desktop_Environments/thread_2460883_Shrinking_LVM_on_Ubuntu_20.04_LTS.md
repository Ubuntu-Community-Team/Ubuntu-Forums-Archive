---
title: "Shrinking LVM on Ubuntu 20.04 LTS"
date: 2021-04-20
forum: Desktop Environments
---

### Post by Drenriza on 2021-04-20
Hi all

A while ago i had a NVME crash in my laptop, and until i had a new NVME from the retailer i have been using a 1TB external USB 3.0 drive
to run Ubuntu from. Now i have the new NVME on 500GB and i am wondering what is the best way to

1. Shrink my current LVM installation (Full encrypted)
2. Move the entire OS with all my settings from my external drive to the new internal drive.

Anyone who have some experience or tips and tricks they can share on the matter?

Thanks on advance
Best regards!

---

### Post by CelticWarrior on 2021-04-20
Reinstallaling is by far the best option.

---

### Post by Drenriza on 2021-04-21
Why would that be the best option?

---

### Post by CelticWarrior on 2021-04-21
Much faster, fool-proof, installs all the correct packages and schedule trim jobs correctly for NVME, etc. etc.

---

### Post by TheFu on 2021-04-21
> **Drenriza said:**
> Why would that be the best option?

I agree with CelticWarrior.
Encryption adds many complications.  Best to just do a fresh install, then use your backup restore processes to put back your settings, data, configuration. Should take about 30-45 minutes.

If you like, you could do a fresh install, choose encryption, then do a pvmove from the old disk to the new disk while running inside a "Try Ubuntu" environment, but you'll need to know how to manually decrypt the LUKS container, activate the LVM VGs and setup partitions **before** that can be accomplished.

Reducing LUKS containers is a little bit of a black art. There's some simple math required AFTER you've reduced the LVM objects to reduce the LUKS container, then the partition.  It is fairly likely that someone would miscalculate and get the partition, LUKS, and LVM sizes off just a little. There's no validation for the calculations at any step.  OTOH, the tools will allow you to force the resize, possibly dropping data.  Your choice completely.

Much easier to do a fresh install and restore stuff from backups that you want. Much easier.

---

### Post by ActionParsnip on 2021-04-23
+1 for reinstall. Feels like a new jumper. You can restore your user data from your backups

---

