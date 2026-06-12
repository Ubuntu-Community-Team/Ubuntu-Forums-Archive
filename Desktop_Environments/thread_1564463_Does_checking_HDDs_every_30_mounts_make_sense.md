---
title: "Does checking HDDs every 30 mounts make sense?"
date: 2010-08-30
forum: Desktop Environments
---

### Post by oblidor on 2010-08-30
Hi

I have been using Linux since 1996, and have yet to have any file system problems. If I remember correctly the default settings are forced fcsk every 6 months or 30 mounts.

What I'm contesting is the need for having a default setting where a partition gets checked as frequent as every 30 mounts. For a server it is a sensible setting, but for a desktop/laptop user it really isn't.

I guess I boot my computer about 3 times per day (morning, after work and evening). This means the file systems gets checked about every 10 days!! So 10 days vs 6 months doesn't make sense to me. It is extremely annoying when partitions are 500++ Gb as it takes long time to check, even with ext4.

I have tune2fs my partitions to 90 or 120 mounts before checking, but I'm wondering why it isn't a default setting when you create a partition on a non-server distro.

---

