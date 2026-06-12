---
title: "copy/move ktorrent to new install?"
date: 2010-09-08
forum: Desktop Environments
---

### Post by chitowner2 on 2010-09-08
OK, I'm sure this has been dealt with before but my search doesn't find it. Point me there if you know. Otherwise:

How can one resume torrents with ktorrent in a new (NOT upgrade) OS install?

I have tried copying over the rc and session files to matching directories without ktorrent running, but when I start it, I don't get any running torrents.

Thanks,
CT
;)

---

### Post by 3Miro on 2010-09-08
If you still keep the .torrent file, then you can just start the torrent normally, but when  you select a destination, pick the directory where the downloaded files are. ktorrent will detect that, verify that the local files match the info for the torrent and start directly from seeding.

If you don't have the original .torrent, try to see if ktorrent keeps a copy in a .something folder.

---

### Post by chitowner2 on 2010-09-08
Actually I was thinking along those lines myself. I always save the .torrent files until I verify the completed downloads, so that's no big deal.

I'm a bit surprised tho that reconstituting the info from the older .kde in the new one isn't sufficient for ktorrent to just resume, so I must be missing something.

CT

---

