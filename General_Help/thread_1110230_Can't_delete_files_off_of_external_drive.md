---
title: "Can't delete files off of external drive"
date: 2009-03-29
forum: General Help
---

### Post by spaparat on 2009-03-29
I have an external hard drive that is formatted ntfs. It hasn't really given me a problem and came that way so I left it alone.

I tried backing some stuff up to it just by simply dragging it. It copied okay until it just froze. So I cancelled it.

Now the folder is empty, but when I type in the ls command it lists a bunch of stuff. If I use the rm command on any of the stuff it says 

"rm: cannot remove directory `steve/Music/Beirut': Input/output error"

I tried running the ntfsfix command in ntfsprogs but that did nothing. How do I get rid of these files?

---

### Post by dacorr on 2009-03-29
Have you tried unmounting then remounting the partition to refresh the directory structure?

---

### Post by hyper_ch on 2009-03-29
you need ntfs-3g to be able to write to ntfs (and delete)

---

### Post by hyperdude111 on 2009-03-29
> **hyper_ch said:**
> you need ntfs-3g to be able to write to ntfs (and delete)

That was years ago (2-3). It now works out of the box.

---

### Post by hyper_ch on 2009-03-29
I have my doubts that an ubuntu installation mounts ntfs drives with read/write by default.

---

### Post by spaparat on 2009-03-29
I have tried unmounting/remounting and restarting my computer.

And ntfs support does come out of box, I copy to and from the drive all the time.

I can still copy to and from the drive, its just these folders won't delete.

---

### Post by dashti on 2010-05-13
I have the same problem! please help!

---

