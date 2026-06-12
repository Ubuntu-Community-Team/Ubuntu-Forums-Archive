---
title: "Network Drive Problems"
date: 2010-05-27
forum: Desktop Environments
---

### Post by cdnjay on 2010-05-27
Hi,

I recently mounted a network drive to my desktop but didn't unmount it before restarting.  Now it appears as just a file on my desktop that can't be deleted and the unmount option no longer exists.  Whenever I try and mount the drive again now numerous windows open and the drive does not appear to mount properly.

Anyone have any ideas?  The drive is shared from an Airport Extreme, I'm connecting via SAMBA I believe.

---

### Post by anglican on 2010-05-28
> **cdnjay said:**
> Hi,

I recently mounted a network drive to my desktop but didn't unmount it before restarting.  Now it appears as just a file on my desktop that can't be deleted and the unmount option no longer exists.  Whenever I try and mount the drive again now numerous windows open and the drive does not appear to mount properly.

Anyone have any ideas?  The drive is shared from an Airport Extreme, I'm connecting via SAMBA I believe.
Open a terminal then:
```
cd ~/Desktop
sudo rm <name_of_unremovable_file>
```H

---

