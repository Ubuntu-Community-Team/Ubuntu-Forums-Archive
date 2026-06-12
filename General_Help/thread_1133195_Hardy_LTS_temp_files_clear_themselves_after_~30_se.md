---
title: "Hardy LTS: temp files clear themselves after ~30 seconds"
date: 2009-04-22
forum: General Help
---

### Post by Gullible Jones on 2009-04-22
Hi... I've installed Xubuntu Hardy LTS on an Acer Aspire 3680 laptop, and it seems well-behaved so far (now that I've switched XOrg from EXA to XAA to prevent crashes). However, there's an issue with temporary files, e.g. archives opened from Firefox without being saved to the hard drive: they disappear after about 30 seconds, even if they're being used (for instance, an archive being extracted).

I think this may be because I've added a line in my /etc/fstab to mount /tmp in RAM:

```

tmpfs /tmp tmpfs nodev,nosuid 0 0
```

However, this really shouldn't cause stuff in /temp to disappear; I've used it on other distros without such problems. Can anyone tell me what's going on?

---

