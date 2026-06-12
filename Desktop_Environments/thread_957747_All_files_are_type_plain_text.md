---
title: "All files are type plain text"
date: 2008-10-24
forum: Desktop Environments
---

### Post by greenbird on 2008-10-24
I'm not sure how it happened but all files suddenly have a type of plain text in nautilus. All types of video and audio files, pdf, MS word, Open Office, etc... all show as plain text. I'm guessing this is a problem with mime types. I did a diff on /usr/share/mime and ~/.mime.types with a backup from before the problem started and there were no changes. Any ideas on where to look for what happened?

---

### Post by signalat on 2008-11-08
> **greenbird said:**
> I'm not sure how it happened but all files suddenly have a type of plain text in nautilus. All types of video and audio files, pdf, MS word, Open Office, etc... all show as plain text. I'm guessing this is a problem with mime types. I did a diff on /usr/share/mime and ~/.mime.types with a backup from before the problem started and there were no changes. Any ideas on where to look for what happened?
I had the same problem after I upgraded from 8.04 to 8.10 a week ago.
can not figure how to fix that problem yet.

---

### Post by greenbird on 2008-11-20
I managed to fix this by reinstalling the following packages:
shared-mime-info
nautilus
nautilus-data
nautilus-share

I did them all at once. I'm not positive but I'm pretty sure that the first one is what fixed it since it reinstalls the files under the /usr/share/mime directory

---

