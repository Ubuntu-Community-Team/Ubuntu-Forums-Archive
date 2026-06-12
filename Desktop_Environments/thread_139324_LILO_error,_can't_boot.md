---
title: "LILO error, can't boot"
date: 2006-03-03
forum: Desktop Environments
---

### Post by cdanr on 2006-03-03
When I attempted to boot up this morning I got the following error from LILO:

Loading LinuxEBDA is big; kernel setup stack overlaps LILO second stage

I tried booting with the installer CD in rescue mode then running /sbin/lilo and although it says boot block written when I reboot I get the same error.

I'm a bit of a noob. Does anyone have any suggestions as to how I might be able to recover my system? 

Thanks

---

### Post by suRoot on 2006-03-03
Did you build your own kernel?  If so, did you enable LARGE_EBDA?

---

### Post by cdanr on 2006-03-03
Thanks for the reply. No, the kernel was updated automatically by the update manager. I didn't make any specific settings.

Cheers

---

