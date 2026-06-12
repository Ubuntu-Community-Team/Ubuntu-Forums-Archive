---
title: "Problem getting to a Windows installation after apt-get dist-upgrade"
date: 2005-12-14
forum: Desktop Environments
---

### Post by dave uk on 2005-12-14
Hi

I just did an apt-get dist-upgrade on my preview of breezy and everything seemed to work ok, but when I rebooted it had removed my Windows XP partition from the GRUB boot loader.

I cant find an easy guide to getting this back, can anyone help?

Thanks
Dave

---

### Post by aysiu on 2005-12-14
If Windows is on the first partition, it's very likely the entry should look like this: ```
title           Windows XP
root            (hd0,0)
savedefault
makeactive
chainloader     +1

```

---

