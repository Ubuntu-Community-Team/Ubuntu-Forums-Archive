---
title: "Would it work to symlink steam program files directory?"
date: 2008-02-01
forum: Gaming &amp; Leisure
---

### Post by B-Con on 2008-02-01
My OS partition is about 16 GB, which is large enough to house the XGB of my Steam files but it makes the filesystem kind of cramped.

Would it be possible to put my steam files, or for that matter all of my Wine files, on a different drive and symlink "~/.wine/drive_c/Program Files" to a folder on a different drive? Would using a symlink cause any problems in this case? I considered mounting a partition to this point, but doing so would be hard and awkward for me to pull off with my current partition table.

---

### Post by diaa on 2008-02-01
I'm not sure I understand the question exactly.
but as far as I know you can use symlinks to directories on other drives(provided that they're mounted on the filesystem) I'm doing this for some of my *Application Data* folders(Pidgin, Firefox) and it's working fine, so I think you can do the same.

---

### Post by B-Con on 2008-02-01
> **diaa said:**
> I'm not sure I understand the question exactly.
but as far as I know you can use symlinks to directories on other drives(provided that they're mounted on the filesystem) I'm doing this for some of my *Application Data* folders(Pidgin, Firefox) and it's working fine, so I think you can do the same.
Yeah, that's basically what I want to do. I know symlinks have restrictions, and I didn't know if it worked so well you could move an entire folder of app data elsewhere and just point a symlink to it in the old spot.

---

