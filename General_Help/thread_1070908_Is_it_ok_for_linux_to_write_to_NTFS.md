---
title: "Is it ok for linux to write to NTFS?"
date: 2009-02-15
forum: General Help
---

### Post by Alekth on 2009-02-15
I have more than a TB data with no real convenient way to backup, it's on NTFS-formatted partitions. Linux seems to be doing fine both reading and writing that, but is there any harm in keeping it that way?

It's just storage, no system data or programs, and I can boot up into Windows every now and then to defragment.
Or should I really shift and backup things to free up the partitions and format to a Linux filesystem?

---

### Post by cosine352 on 2009-02-15
I think you are fine.

---

### Post by aktiwers on 2009-02-15
You will be fine. The ntfs-3g driver has been stable for more than 1 year now.

---

### Post by geirha on 2009-02-15
Linux will read and write to NTFS quite safely. Alot of people have a setup similar to yours, where they use NTFS partitions as a place to store files that can be read by both operating systems. Linux is unable to do more advanced things like fixing filesystem errors and such though, you'll need to have Windows take care of that.

But backup regularly. Hard drives don't last for ever.

---

### Post by Alekth on 2009-02-15
Thanks :)

---

### Post by binbash on 2009-02-15
It will be fine

---

