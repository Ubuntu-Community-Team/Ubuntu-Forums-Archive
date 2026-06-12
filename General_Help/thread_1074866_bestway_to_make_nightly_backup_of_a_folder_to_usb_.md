---
title: "bestway to make nightly backup of a folder to usb drive?"
date: 2009-02-19
forum: General Help
---

### Post by lime4x4 on 2009-02-19
Currently running ubuntu intrepid 8.10. Recently bought a 1 tb usb external drive. Would like to do a nightly backup of my photo folder to my usb hard drive every night and only replace files that have been changed or added

---

### Post by CrucifiedEgo on 2009-02-19
I'm sure there's a GUI app that does something similar, but I would use cron to schedule the backup using rsync.  This article covers the subject pretty well: [http://www.linux.com/feature/117236](http://www.linux.com/feature/117236)

---

