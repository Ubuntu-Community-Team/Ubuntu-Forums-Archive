---
title: "When installing Ubuntu, does it make sense to unplug all but main drive?"
date: 2009-04-05
forum: General Help
---

### Post by Roasted on 2009-04-05
I've had a habit of doing this for years, and more recently I'm questioning my habits with it.

I have 4 hard drives in my computer, all of them SATA. The main drive dual boots Vista/Ubuntu, where the other 3 drives are backup drives. Whenever I've reinstalled Ubuntu, I've done it with the other 3 drives unplugged and later added them to /etc/fstab.

My buddy had two drives in his computer, one dual booting XP and Ubuntu, the other is a backup drive. He unplugged his backup drive and wanted to boot on the main drive only and he got a grub error. When he plugged the backup drive back in, it worked fine.

To me, this is a nuisance. If a backup drive dies, I still want to be able to boot my system.

What exactly happens here that causes Ubuntu not to boot if a secondary backup drive with no OS on it isn't present?

---

### Post by lisati on 2009-04-05
I've been known to unplug USB hard drives when tinkering with what OS is installed on my machine. It was mainly to help avoid loss of data in case of stuff up on my part.

---

