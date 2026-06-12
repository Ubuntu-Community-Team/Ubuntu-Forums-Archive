---
title: "ltsp-build-client problem"
date: 2005-10-25
forum: Desktop Environments
---

### Post by eliasg on 2005-10-25
Hi everyone,

I am having a problem while trying to execute ltsp-build-client in my breezy 5.10 (updated from 5.04). After execute  'sudo ltsp-build-client', this error appear:

I: Retrieving Release
E: Failed getting release file [http://us.archive.ubuntu.com/ubuntu/dists/breezy/Release](http://us.archive.ubuntu.com/ubuntu/dists/breezy/Release)

any ideas?
Thank you in advance

Elias

---

### Post by SteveGatenby on 2005-12-23
Elias - dont know if its any help - 
I had the same prob till I found that of my two network cards, the system is always defaulting to eth0 as the default gateway device (under System/Admin/Networking) - my internet connection is on eth1 and therefore couldn't access outside of my local network for updating

---

