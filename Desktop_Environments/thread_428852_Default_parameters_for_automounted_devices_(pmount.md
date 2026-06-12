---
title: "Default parameters for automounted devices (pmount, mtab)"
date: 2007-04-30
forum: Desktop Environments
---

### Post by ntt on 2007-04-30
Hi,

since I've upgraded to Kubuntu Feisty Fawn (7.04), my USB external hard disk became slow as hell.

I've investigated the problem and discovered that it's now automounted with the 'sync' option (as shown in /etc/mtab while it's mounted), which explains the ridiculous performance.

But I don't know how/where to modify the default parameters for the automount service, so that I can specify to mount USB devices (or at least THAT USB hard disk) with the 'async' option.

Thanks in advance for any hints.

---

