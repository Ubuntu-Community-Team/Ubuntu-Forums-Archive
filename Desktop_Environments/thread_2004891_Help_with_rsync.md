---
title: "Help with rsync"
date: 2012-06-16
forum: Desktop Environments
---

### Post by Alligator on 2012-06-16
I'm trying to backup to a usb drive using rsync. I've tried various options of rsync (see below), but always get error code 23.  I've tried setting up a rsync server (/etc/rsync.conf) without any change.  Here is the script and followed by error message.

#       rsync -az --delete --exclude=/proc --exclude=/sys \
#                                        --exclude=/mnt --exclude=/media \
        
        rsync -rltDvu --dry-run --progress --delete --delete-excluded --exclude-from=backup.lst \
        $location $destination

        echo "Changing Permission, please wait..."
        chown -R ron:ron $destination
__________________________________________________

sent 11964259 bytes  received 61406 bytes  3435904.29 bytes/sec
total size is 53884404491  speedup is 4480.78 (DRY RUN)
rsync error: some files/attrs were not transferred (see previous errors) (code 23) at main.c(1070) [sender=3.0.8]
Changing Permission, please wait...
ron@Ron-WS:~$

---

### Post by SeijiSensei on 2012-06-16
My guess is that the backup drive is formatted with a Windows filesystem like FAT32 or NTFS.  Rsync expects a "POSIX" filesystem like ext[234].  The easiest solution is to reformat the USB drive to ext4.  Otherwise you're stuck with using tar and writing an archive tarball to the USB drive.

---

### Post by Alligator on 2012-06-16
The usb drive is formated with ext3 file system.

---

### Post by SeijiSensei on 2012-06-16
I see the root prompt character ("#") in the original, but I'm wondering whether you actually ran the command as root.  Did you use "sudo rsync ...."?

---

### Post by markbl on 2012-06-17
BTW, rather than add those explicit excludes for the pseudo & other file systems as you have done, you may want to consider just adding "-x" which will automatically do that for you. Ignore this tip if you knew it and added all those explicitly for some other reason.

---

### Post by Alligator on 2012-06-17
The script is run as sudo, in fact, it echo's an error message if not.  I went with the backup list rather than more excludes, to avoid typo's.  I've tried more than these two examples and I discovered using the 'dry-run' option saves time.  Fortunately I haven't had to restore my desktop, despite having both mirrored hd's crashing within a day or two of the other. hence my need for a working accurate backup.  Never buy two drives made in same production line, what are the odds?

---

### Post by firekage on 2012-06-17
> **markbl said:**
> BTW, rather than add those explicit excludes for the pseudo & other file systems as you have done, you may want to consider just adding "-x" which will automatically do that for you. Ignore this tip if you knew it and added all those explicitly for some other reason.

Can You writhe his "set up" with this -x thing? I don't know it, would like to learn it.

---

### Post by markbl on 2012-06-17
> **firekage said:**
> Can You writhe his "set up" with this -x thing? I don't know it, would like to learn it.
See man rsync. I often see people quote similar examples for rsync when copying the root partition they add a heap of "--exclude=/proc --exclude=/dev --exclude=/media" etc but all that is redundant if you just add "-x" instead because they are all on different file-systems and "-x" stops rsync from traversing to different file-systems anyhow. All those "--exclude" options he adds in his first post can be replaced with a simple "-x" (which will also catch any he may have missed btw, now and in the future).

---

### Post by Alligator on 2012-06-17
I added --log-file=FILE to the following:
rsync -rltDvu --dry-run --progress --log-file=/tmp/backupshit.txt --delete --delete-excluded --exclude-from=backup.lst \
        $location $destination

I discovered only one error in the log relating to .gvfs, added to the backup.lst and it works without the error code 23.  Time to remove the dry-run.

---

