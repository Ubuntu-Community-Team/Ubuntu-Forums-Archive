---
title: "media sub-sirectory user name"
date: 2017-04-03
forum: Desktop Environments
---

### Post by dwlamb on 2017-04-03
I am having a challenge finding a topic I know I have seen previously.  I only encounter it when installing a new version of Ubuntu or a derivative. 

Starting with 14.04 I think, a user's name appears in the /media subdirectory and all removable media (e.g., USB drives) hang off that user name sub-directory instead of simply /media.  There is a script one can copy and paste in the command line to return the behaviour back to simply /media.

I really need this old behaviour for drives I connect on the fly.

---

### Post by TheFu on 2017-04-03
Don't know about anything specifically as you describe, but you can create a script that mounts anything where you want it.  I use the partition label to do this.

Just set the LABELs to match the labels for the partitions you want to mount and the UID/GUI to match mine.  I put temporary mounts under /mnt/ - old habit. LABEL 1/2 are probably NTFS partitions. All the others are flash drives with FAT32 partitions.  For Linux file systems, I use automount/autofs to deal with the mounting 'as-needed' (connect and access).
```

sudo mkdir -p /mnt/$LABEL1 /mnt/$LABEL2 /mnt/$LABEL3 /mnt/$LABEL4 \
/mnt/$LABEL5 /mnt/$LABEL6 /mnt/$LABEL7
sudo mount -o uid=$UID,gid=$GID LABEL=$LABEL1 /mnt/$LABEL1
sudo mount -o uid=$UID,gid=$GID LABEL=$LABEL2 /mnt/$LABEL2
sudo mount -t vfat -o uid=$UID,gid=$GID LABEL=$LABEL3 /mnt/$LABEL3
sudo mount -t vfat -o uid=$UID,gid=$GID LABEL=$LABEL4 /mnt/$LABEL4
sudo mount -t vfat -o uid=$UID,gid=$GID LABEL=$LABEL5 /mnt/$LABEL5
sudo mount -t vfat -o uid=$UID,gid=$GID LABEL=$LABEL6 /mnt/$LABEL6
sudo mount -t vfat -o uid=$UID,gid=$GID LABEL=$LABEL7 /mnt/$LABEL7
```

Of course, this script isn't automatic. It has to be run, but I suppose I could make it run whenever a new storage device is seen by the udev rules.

---

