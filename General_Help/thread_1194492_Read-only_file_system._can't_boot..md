---
title: "Read-only file system. can't boot."
date: 2009-06-22
forum: General Help
---

### Post by zoopside on 2009-06-22
Hello,
[EDIT] Sorry for the incorrect title. I CAN boot, but cannot startx [/EDIT]

I recently rebooted to the message that X11 couldn't start. When looking at the boot messages most contain an error message followed by "Read-only file system". I've googled my various messages and tried the following :

1. boot to liveCD, run fsck (-y -f) ```
sudo fsck /dev/sda6 -y -f
``` on all ubuntu partitions.
     This step went without a hitch, with fsck reporting no errors.
2. boot to recovery console and attempt to remount the partition via :
 ```
sudo mount -no remount,rw /
```
this remount works fine, and I am then able to make changes to the filesystem.

Why would the initial mount fail to mount in rw, but then I can remount later rw? And what other debug steps would anyone recommend? Thanks much beforehand for any help.

---

### Post by michy99 on 2009-06-22
You probably have a line in fstab that includes 'errors=remount-ro' This mounts the partion as read-only if there are any errors on mounting. The problem is figuring out what is causing the errors to begin with.

---

### Post by zoopside on 2009-06-22
I most certainly do have that line. Without much hope I tried to flip it to remount-rw, but that didn't work. What also makes this a bit hard is that the log files aren't being written due to the Read-only filesystem (i.e. I can see dmesg unable to log). Do you have any ideas on how I would find out what the mount error on boot is?

---

### Post by michy99 on 2009-06-22
I'm afraid I'm not much help in that department. Hopefully someone wiser than I will come along.

---

### Post by MrPasty on 2009-06-22
I have the same problem. Got it after rebooting when I had updated to the latest kernel. Hope someone comes up with a solution. Until then, I'll try to do exactly what you have done to see if I can figure something out. Wouldn't count on it, though, as I'm fairly new to Linux.

---

