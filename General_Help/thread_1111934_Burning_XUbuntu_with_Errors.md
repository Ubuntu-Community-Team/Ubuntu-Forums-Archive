---
title: "Burning XUbuntu with Errors"
date: 2009-03-31
forum: General Help
---

### Post by jwh400 on 2009-03-31
I'm getting the 8.10-desktop-i386  iso from the XUbuntu site and burning with Brasero 0.7.1. I've tried twice with different iso's but get an error message at the end after the disc check. I'm burning at 8x. Here are the last few lines of the session log. If you need the entire log I'll host it elsewhere and post a link here since it's rather lengthy.

```
BraseroReadom finished track successfully
BraseroReadom got killed
BraseroReadom disconnecting BraseroReadom from BraseroMd5sum
BraseroReadom deactivating
BraseroMd5sum called brasero_job_get_action
BraseroMd5sum called brasero_job_get_current_track
BraseroMd5sum setting new checksum (type = 1) cf10f53f800d845cda78e2b7f01f5531 (53c50ff06f4ad659f0abf6474b58c8e6 before)
BraseroMd5sum called brasero_job_error
BraseroMd5sum finished with an error
BraseroMd5sum asked to stop because of an error
    error        = 22
    message    = "some files may be corrupted on the disc"
BraseroMd5sum stopping
BraseroMd5sum closing connection for BraseroMd5sum
Session error : some files may be corrupted on the disc (brasero_burn_record burn.c:2270)
```A friend is migrating to Linux and has chosen Xubuntu for his laptop. I've burned many copies of Ubuntu without errors so I'm thinking there might be an iso problem (?).
:)

---

### Post by jwh400 on 2009-03-31
I'm sorry if I'm wrong for bumping this but I posted it this morning just after I was getting a database error here and when the post showed up it was buried on page 5.

---

### Post by SikEnCide on 2009-03-31
are you burning the ISO as slow as possable?  try burning something else to verify it is not your burner. try a different iso image.

---

### Post by jwh400 on 2009-03-31
> **SikEnCide said:**
> are you burning the ISO as slow as possable?  try burning something else to verify it is not your burner. try a different iso image.

Yes, burning at the minimum which varies from 3x to 6x during the burn. I just finished burning Ubuntu 8.10 with no errors. I immediately tried XUbuntu with yet another iso from the XUbuntu site but finished with the same error message. :cry:

---

