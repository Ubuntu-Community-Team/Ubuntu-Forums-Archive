---
title: "Hangs at boot mounting CIFS shares"
date: 2012-01-29
forum: Desktop Environments
---

### Post by JerkyChew on 2012-01-29
This has to be a super easy fix, but for the life of me I can't find anything helpful.

I have an Ubuntu 10.10 box that I've just added a ton of cifs mounts to /etc/fstab. I just rebooted it and it complains that it can't mount the folders specified in that fstab file, presumably because the network isn't started yet. 

What's infuriating is, in the past I could hit skip and mount -a on boot and pretend I'd fix it at a later date. However, that's no longer the case. Skipping just hangs the whole system. I'm willing to bet it's because I just moved my MythTV recordings folder to my NAS and MythTV or MySQL or a combination of the two are freaking the heck out because they can't get to that folder. But I'm veering off topic...

Anyhoo, how can I delay the mounting of /etc/fstab until after the network is started?

---

### Post by 2F4U on 2012-01-29
Have you tried setting the mounts to noauto? That would prevent them from being automatically mounted at boot time.

---

