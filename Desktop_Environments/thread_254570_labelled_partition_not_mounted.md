---
title: "labelled partition not mounted"
date: 2006-09-10
forum: Desktop Environments
---

### Post by paulhide on 2006-09-10
I used e2label to label a partition on a sata disk /dev/sda1 with the label ublinux edited fstab to contain:
label=ublinux   /               ext3    defaults,errors=remount-ro 0       1
and this booted correctly.
I made another partition /dev/sda5 and used e2label to label it dyndata, formatted it, made the directory /dydtest and then added another line to fstab:
label=ublinux   /               ext3    defaults,errors=remount-ro 0       1
label=dyndata   /dyntest        ext3    defaults,errors=remount-ro 0       1
On bootup now, the first partition mounts correctly, but the second gives the following error message from fsck.ext3: Unable to resolve 'label=dyndata'.
Does anyone have any thoughts.

Paul Hide

---

