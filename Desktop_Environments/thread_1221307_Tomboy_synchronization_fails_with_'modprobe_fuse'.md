---
title: "Tomboy synchronization fails with 'modprobe fuse'"
date: 2009-07-23
forum: Desktop Environments
---

### Post by cfgauss on 2009-07-23
I have Ubuntu 9.04 AMD64 and have set up a webdav server which works. I'd like Tomboy Notes to synchronize with it. From another post, I downloaded the wdfs tarball and installed it. But when I attempt to synchronize Tomboy, .tomboy.log states "Could not find 'fuse' in lsmod output". In fact fuse isn't in lsmod's output. I read that the current kernel, 2.6.28-13, has fuse built-in and, hence, it's not a module.

Is this correct?

If so, will Tomboy always fail with its 'lsmod' test? Is there a work-around?

---

### Post by dholbert on 2009-08-06
There's a bug filed on this issue here:
[https://bugs.launchpad.net/ubuntu/+source/tomboy/+bug/345166](https://bugs.launchpad.net/ubuntu/+source/tomboy/+bug/345166)

From glancing over the bug, it looks like there's a patch available upstream, but it's not in the repositories yet.  However, there's a fixed .deb available in a PPA, as noted here:
[https://bugs.launchpad.net/ubuntu/+source/tomboy/+bug/345166/comments/16](https://bugs.launchpad.net/ubuntu/+source/tomboy/+bug/345166/comments/16)

---

