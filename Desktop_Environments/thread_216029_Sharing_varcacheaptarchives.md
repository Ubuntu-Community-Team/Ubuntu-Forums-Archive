---
title: "Sharing /var/cache/apt/archives"
date: 2006-07-14
forum: Desktop Environments
---

### Post by markcarey on 2006-07-14
All,

I have a couple of machines running ubuntu on a shard adsl line, in nz we have nasty monthly data caps.

I am thinking of using nfs to share (rw) /var/cache/apt/archives so that once I have downloaded a deb I can use it across multiple machines.

The alternative is to rsync the contents of this directory to the other machines, although this is a waste of disk space.

Are there any nasty issues with going the nfs route; e.g when performing an upgrade after a reboot the system will look for /var/cache/apt/archives before the network interfaces or nfs services have started?

Thoughts Ubuntu gurus?

Thank you.

Regards,

Mark Carey

---

### Post by markcarey on 2006-07-21
Ok so I have gone down the nfs route and all seems to work .....

---

