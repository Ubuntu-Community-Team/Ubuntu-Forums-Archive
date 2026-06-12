---
title: "wipe /dev/hda1 possible?"
date: 2006-06-27
forum: Desktop Environments
---

### Post by truenemesis on 2006-06-27
is it possible to insert the live CD, install wipe, and then run the following command?

Secure delete the entire harddrive and then install a super fresh install of linux?

---

### Post by rai4shu2 on 2006-06-27
If you do use wipe or shred (or some other tool like that), there are a few small items to keep in mind.

1. This is only necessary if you plan on sending your drive to some untrusted person who may take your data (and the data is something you cannot afford to share).

2. Modern hard drives can transparently remap sectors or could even conceivably detect a wipe attempt and thwart it.

3. If you have sensitive data, your best option is to encrypt it with a strong password. Wipe is only mostly effective against casual intrusion, but a serious forensic team can probably find data even on a wiped drive.

---

### Post by truenemesis on 2006-06-27
thanks. so whats the best way to ensure that a harddrive's data after being deleted is not readable? Partition it 6-7 times over?

---

### Post by rai4shu2 on 2006-06-27
To destroy data without destroying the drive is difficult. Partitioning multiple times would be less effective than using wipe.

Of course, the best way to secure your data is to either use encryption or put your hard drive in a bank vault when you're done with it.

---

