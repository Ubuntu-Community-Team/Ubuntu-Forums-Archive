---
title: "Backup boot,root,home in order to restore later"
date: 2005-01-19
forum: General Help
---

### Post by giorgosc61 on 2005-01-19
Hello. I have set up ubuntu with all the applications I want.
My system is set:
hda1: /boot (ext2)
hda5: / (ext3)
hda6: /home (ext3)
hda7: /swap 
How can I backup by creating a tar on eg hda8(ext3) all the above except swap in order to restore the system by running a livecd?

---

### Post by mendicant on 2005-01-19
You can boot from your livecd, then mount the partitions read-only (hda1-hda6), mount hda8 rw, then make the tarballs to hda8.

---

### Post by mendicant on 2005-01-19
So, the actual commands are something like:
## boot from cd
## ensure you have enough room on /dev/hda8 for /dev/hda{1,5,6}
% mkdir -p /tmp/{root,home,boot}
% mount -t ext2 -o ro /dev/hda1 /tmp/boot
% mount -t ext3 -o ro /dev/hda5 /tmp/root
% mount -t ext3 -o ro /dev/hda6 /tmp/home
% mkdir /tmp/backup
% mke2fs -j /dev/hda8 # assuming you want a new partition for this, skip otherwise
% mount -t ext3 -o rw /dev/hda8 /tmp/backup
% ## depending on if you have enough space on hda8, you may need to add the -j or -z flag
% ## for bzip compression and gzip compression, respectively
% tar -cf /tmp/backup/root.backup.tar /tmp/root
% tar -cf /tmp/backup/boot.backup.tar /tmp/boot
% tar -cf /tmp/backup/home.backup.tar /tmp/home
% ## so for example, use tar -czf /tmp/backup/root.backup.tar.gz /tmp/root
% ## or tar -cjf /tmp/backup/root.backup.tar.bz2 /tmp/root for compression
% umount /tmp/backup
% umount /tmp/root
% umount /tmp/boot
% umount /tmp/home
% ## and you're done

---

### Post by giorgosc61 on 2005-01-20
Thank you for your answers.
Should it be better to tar -cjpf instead of tar -cf ?
By having these backups on a dvdr can I with a livecd put a new hard disk and create the system I had previously with a livecd without using ubuntu installation cd?

---

### Post by mendicant on 2005-01-20
Assuming you're doing it as root, the -p flag is unnecessary.

The -j flag is fine if you think you'll need it for space on hda8, but will be faster without it (for both backup and restore).  If you can get away with just gzip compression, -z will also be faster than -j.

---

