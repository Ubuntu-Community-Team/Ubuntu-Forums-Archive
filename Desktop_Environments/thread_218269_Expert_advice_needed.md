---
title: "Expert advice needed"
date: 2006-07-18
forum: Desktop Environments
---

### Post by ml1710 on 2006-07-18
Hi!

I'm having a lot of trouble getting wake on lan enabled.

It worked fine on Debian Stable (with kernel 2.4) but not with kernel 2.6 on Ubuntu.  I have a 3com 905b onboard network adaptor (Dell Gx1 computer), which was able to wake on lan (in Debian) by adding "options 3c59x enable_wol=1" to a /etc/modutils/ file.

So far I've tried everything to get it to work with Ubuntu . I've added the same options to a /etc/modprobe.d file, enabled acpi, tried modprobe, ethtool, etc, but it still doesn't work.  Also something to note is that when I upgraded my Debian kernel from 2.4 to 2.6 it didn't work either.  Maybe it isn't passing the module options along.

Does anyone have any ideas?  I have been looking for information for two weeks, and any information would be appreciated!

Thanks!

---

