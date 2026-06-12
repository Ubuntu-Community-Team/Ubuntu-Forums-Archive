---
title: "File Manager"
date: 2006-02-21
forum: Desktop Environments
---

### Post by Jaybird on 2006-02-21
Why is it that I cannot create a folder on a partitioned drive while in file manager?  The only way I found to create a folder on one of these partitions is to sign in as root or do what I did, chown the partition to me as a user.

---

### Post by cskeide on 2006-02-21
Is this a linux native partition, or Windows FAT?

---

### Post by Jaybird on 2006-02-21
Linux, ext3 in fact.  I can write to them, but I can't create the folder nor can I burn from them apparently as I just found out.

---

### Post by cskeide on 2006-02-21
I guess if these partitions are auto-mounted at boot, the best way is to change group ownership to for example 'users' and give this group write permissions.

chown root.users /mountpoint
chmod 775 /mountpoint

Or, if I'm not mistaken, you could disable auto-mount in /etc/fstab and add the users option, which will allow users to mount and read/write.

Not sure if this is the solution you were looking for, though.

---

### Post by Jaybird on 2006-02-21
chown on the mount point did it.  thanks.  The partition is in /media/hda7 and I had chown'd the hda7, but not the media.  Now I'm happy.  Once again thanks.

---

