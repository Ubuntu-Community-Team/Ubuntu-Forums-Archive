---
title: "Move Ubuntu to new hdd without reinstall need advice"
date: 2009-01-25
forum: General Help
---

### Post by rativid on 2009-01-25
I need to move my Ubuntu from old HDD to new. I decide using dd to copy MBR and rsync to copy files from old hdd to new. Maybe exist better way to do this?

---

### Post by adamlau on 2009-01-25
Clonezilla.

---

### Post by Alterax on 2009-01-25
Being a lazy man. I'm tempted to say your best bet is to make dd do all the work for you.  Pop the case on the computer and put in the new hard drive as a slave drive.

Boot off the live CD, and when it comes up to the desktop, open a terminal.

run the following:

```
sudo dd if=/dev/sda of=/dev/sdb bs=2048 &
```

Let it do its thing.  You may have to use hda and hdb as tags instead of sda and sdb, depending on the liveCD version you're using.  Just MAKE SURE the original drive is in the master position and the new drive is in the slave position; you don't want to overwrite your original.

when that is done, use the partition editor on the new drive to resize the partitions as you see fit.  Finally, shut it down, remove the old drive, and move the new drive to the master position.  You're done.

---

### Post by rativid on 2009-01-25
Thanks for advise, I will try it. I forgot say that I changing hdd on my laptop and new hdd I’v connect through USB external box.

---

