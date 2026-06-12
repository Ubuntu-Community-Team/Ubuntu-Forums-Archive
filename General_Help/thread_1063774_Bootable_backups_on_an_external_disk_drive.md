---
title: "Bootable backups on an external disk drive"
date: 2009-02-08
forum: General Help
---

### Post by jouni on 2009-02-08
I have been making backups to an external drive with an eSATA-SATA converter by running a script that basically does

```
  rsync --archive --one-file-system --delete \
    --exclude=/tmp --exclude=/var/tmp \
    / /mnt/rootbackup
```

(and similarly for /boot). I use LVM on both the internal drive and the backup drive, using different volume group names so that I can mount the backup partitions via /dev/mapper.

Now my internal drive died, so I installed the external drive inside the computer and booted using the install CD in rescue mode. On the assumption that various configuration files may include the volume group name, I renamed the volume group using first lvchange -an on the logical volume, them vgrename on the volume group, and then lvchange -ay on the logical volume. I created a swap partition on the drive and the /tmp and /var/tmp directories (after having spent quite some time wondering why e.g. grub-install shows error messages referring to tempnam). I edited /etc/fstab to point to the backup partitions (I got the UUIDs using tune2fs -l) and ran update-grub and grub-install /dev/sda. Then I was able to boot (and after fixing the permissions of /tmp, I could even run a Gnome session). (I had also edited /boot/grub/menu.lst before I realized that update-grub gets its information from /etc/fstab, but I think that this had no effect in the end.)

My questions are: First, although everything seems to be working fine, is there something I may have overlooked?

Second, since I will be doing backups to a new external drive, what can I do differently to make booting from that drive easier? Obviously I should exclude /tmp/* instead of /tmp so that I get a  /tmp directory on the backup. I could create a swap partition on the backup drive and add to my backup script some command to edit /etc/fstab on the backup so that it refers to the correct partitions. But how can I install grub on the backup disk? It seems to me that update-grub assumes the current configuration is the one that will be booted, which is not true in this case.

---

