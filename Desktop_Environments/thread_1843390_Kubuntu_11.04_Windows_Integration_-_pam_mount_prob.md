---
title: "Kubuntu 11.04 Windows Integration - pam_mount problem : sudo unmount shares"
date: 2011-09-13
forum: Desktop Environments
---

### Post by pivert on 2011-09-13
Hi,

I set up my Kubuntu Desktop to integrate with our Microsoft Windows AD using Likewise-open (6.0.0.53010-4ubuntu5.1), and pam_mount to mount the shares. (This was not that easy, mainly due to the lack of a concise up to date documentation).

My network shares are automatically mounted via pam_mount.

When I sudo -i in a konsole, pam_mount unmount the network shares.

How can I prevent other users (such as root) to trigger pam_mount ?

Thanks,

---

