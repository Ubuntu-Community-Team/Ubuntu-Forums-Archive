---
title: "XPS m1330 Eject button doesn't work."
date: 2008-12-07
forum: Dell Ubuntu Support (CLOSED)
---

### Post by x C0MMAND0 x on 2008-12-07
Topic, and I have tried [this link]("https://bugs.launchpad.net/ubuntu/+bug/180866"), but it did not work.

---

### Post by damis648 on 2008-12-07
Simply add this to /etc/sysctl.conf:

```
# Unlock the CDROM eject button
dev.cdrom.lock=0
```

You have to restart for it to take effect.

---

### Post by x C0MMAND0 x on 2008-12-07
After the reboot it worked, thanks.  But, now there is still the DVD icon on the desktop, and I can't unmount it because, "no media is in the drive".  Is there a workaround for this?

---

