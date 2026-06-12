---
title: "Zip drive doesn't write immediately"
date: 2009-04-21
forum: General Help
---

### Post by peyre on 2009-04-21
When I copy files to a zip disk, it holds the changes in cache and doesn't actually write to the disk until I tell it to eject.  Trouble is that since zip drives are so slow, it times out and whines that it can't eject the disk.

Is there some setting I can change to have the OS write to the disk immediately instead of waiting for a [font="Courier New"]umount[/font] command?

---

### Post by StuartN on 2009-04-21
The command "sync" will flush all the file buffers. I don't know if "mount -o sync" (which is supposed to mount the drive without a buffer) would work for you.

---

