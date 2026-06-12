---
title: "How to umount /tmp, /usr, /var and /home"
date: 2009-05-04
forum: General Help
---

### Post by pirattrev on 2009-05-04
Let me preface this by saying that my drive is severely messed up. in order to cope with the massive number of badblocks and severe damage I've reinstalled my computer with Jaunty 9.04 but have divided the drive into many independent sections, with a volume for each major mount point, and the majority of my drive devoted to large fat32 chunks that are easily unmounted. I've done this because the micromanaging has helped me in the past deal with this problem and fat32 volumes are very easy to deal with if problems arise (They can be unmounted as pure information volumes and their corrupt clusters can be weeded out). However I am unable to unmount my /var, /usr, /tmp and /home partitions because they are in use. Is there a method that anyone knows to fix these volumes, blacklist the bad blocks, and still maintain information? [they are all set to the new ext4]

---

### Post by pirattrev on 2009-05-04
Bump

---

### Post by delcypher on 2009-05-04
I can't quite see your logic installing more stuff (like ubuntu) on an already damaged drive. It would be better to use a live cd and sort out your hard drive problems from there (On a live cd either none of your drives will be mounted or they'll be easy to unmount).

You can't unmount /tmp /usr/ or /var they are not filesystems (they are all part of the root (/) filesystem). You can't really unmount the root file system (/), I have a feeling umount won't let you and with good reason, you're using it!

However varrun and varlock are seperate filesystems. Though I'm not sure if it's a good idea to unmount them.

Anyway to list mounted file systems type the following into the terminal ```
mount
```

This command also is quite useful (shows disk usage and filesystem name)```
df -h
```

This command is also quite useful, it lists physical disks attached to your system.
```
sudo fdisk -l
```

#To unmount a filesystem type ```
sudo umount [device_name_or_mount_point]
#e.g. to umount /home/ located on my system /dev/sda2
sudo umount /dev/sda2
# The command below should have the same effect
sudo umount /home/
```

Out of interest what tools are you planning to use on your damaged partitions?

---

### Post by dcstar on 2009-05-04
> **pirattrev said:**
> Let me preface this by saying that my drive is severely messed up. in order to cope with the massive number of badblocks and severe damage I've reinstalled my computer with Jaunty 9.04 but have divided the drive into many independent sections, with a volume for each major mount point, and the majority of my drive devoted to large fat32 chunks that are easily unmounted. I've done this because the micromanaging has helped me in the past deal with this problem and fat32 volumes are very easy to deal with if problems arise (They can be unmounted as pure information volumes and their corrupt clusters can be weeded out). However I am unable to unmount my /var, /usr, /tmp and /home partitions because they are in use. Is there a method that anyone knows to fix these volumes, blacklist the bad blocks, and still maintain information? [they are all set to the new ext4]

As with the hundreds of posts that have stated this previously, boot off a Live CD.

---

### Post by delcypher on 2009-05-04
Also seeing as you've formated in MS's format wouldn't Microsoft's ```
chkdsk /R C:
```

from a xp/vista setup cd do a much better job?

---

