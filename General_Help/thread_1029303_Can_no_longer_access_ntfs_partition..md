---
title: "Can no longer access ntfs partition."
date: 2009-01-03
forum: General Help
---

### Post by ghostrc79 on 2009-01-03
Hi

I have turned on my laptop today and when I try to access my media/X ntfs partition it is telling me it is unable to mount the volume X. Its been working fine for about a month since I last did a fresh install. Any ideas on how to fix it?

Many thanks and happy new year

Matt

---

### Post by taurus on 2009-01-03
The last time you used windows, did you shut it down cleanly?

What are the outputs of these commands from a terminal?

Applications -> Accessories -> Terminal
```
sudo fdisk -l
cat /etc/fstab
df -h
```

---

### Post by ghostrc79 on 2009-01-03
Ha, that was it, stupid vista did not shut down properly. Booted up, shut it down all happy again.

Thanks for your help:KS

---

