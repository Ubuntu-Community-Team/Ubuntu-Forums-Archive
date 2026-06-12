---
title: "ubuntu install upset XP"
date: 2009-01-18
forum: General Help
---

### Post by Raccoon1400 on 2009-01-18
Just installed ubuntu on my desktop.
it has a 40GB master drive, with a windows and linux partition, and swap
and an ntfs slave drive

I previously had pclos installed, and I installed ubuntu using the same partitions.

When I boot windows, I get the hourglass for much longer than usual on startup. When I go into my computer, it shows the flashlight for a while before showing files.

At first, I thought it may have been the windows ext2 drives, but removing those didn't help.

What happened to my system and how can I fix it?
I'm sure I didn't format partitions I didn't want to.

---

### Post by Ptero-4 on 2009-01-18
You probably need to do a chkdsk (use ntfsfix from linux to mark the windows volume for boot-time filesystem consistency check. Then run the defragmenter (XP's defragmenter doesn't run automatically). This should (temporarily) clear up XP's normal slugginess.

---

### Post by Raccoon1400 on 2009-01-18
I tried chkdsk. It corrected some errors on the slave, but the problem persists.
This is not XP's normal sluginess. Is started doing this all of a sudden.

I'm not sure it was ubuntu that did it anymore. I used photorec on systemrecoverycd to recover files from an external HD, and it used all but .5GB on the HD. It could be either.

---

### Post by Raccoon1400 on 2009-01-18
I fould the culprit. I removed some resoration software I was using and that seems to have fixed it.

---

