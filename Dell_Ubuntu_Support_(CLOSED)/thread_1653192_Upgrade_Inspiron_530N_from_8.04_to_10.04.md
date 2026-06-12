---
title: "Upgrade Inspiron 530N from 8.04 to 10.04"
date: 2010-12-26
forum: Dell Ubuntu Support (CLOSED)
---

### Post by kryos on 2010-12-26
I have run a live cd without problems but am hesitant to upgrade via update manager or other non Dell means.  May be a clean install is in order or just leave well enough alone?

---

### Post by gbrainin on 2010-12-26
On my 530, I have clean-installed nearly every version from 8.04 to 10.04 with few problems.  There is the issue regarding the RAID vs. IDE setting in the BIOS; I forget which versions that applied to, but if you find a boot failure where you get dropped into the "busybox," try switching that setting.

Obviously, you want to be sure you save your user data, either by backing up or having it on a separate partition.

On the other hand, updating via the update manager does usually work, and if it doesn't, well, you were going to do a clean install anyway.

---

