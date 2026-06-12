---
title: "Invisible partition?"
date: 2006-09-29
forum: Desktop Environments
---

### Post by stephenisu on 2006-09-29
Out of curiosity I was just looking at my partitions in the System => Administration => Disks area and it showed that my root file system was unformatted/unaccessable.  This wouldn't seem so odd if the machine was broken, so i ran the following from the terminal to get more info

```
# df -h -T
```

and got:

```

[FONT="Courier New"]                ext3    73G   11G   59G  15% /
varrun       tmpfs    125M   88K  125M   1% /var/run
varlock      tmpfs    125M  4.0K  125M   1% /var/lock
udev           tmpfs    125M  124K  125M   1% /dev
devshm       tmpfs    125M     0  125M   0% /dev/shm
lrm            tmpfs    125M   19M  107M  15% /lib/modules/2.6.15-26-386/volatile
/dev/hda5     ext3    228M   14M  203M   7% /boot
/dev/hdb1     vfat     18G   13G  5.5G  70% /media/0 GB Disk (hdb1)
/dev/hdb7     vfat    9.3G  8.4G  991M  90% /media/0 GB Disk (hdb7)
/dev/hdc   iso9660    4.1G  4.1G     0 100% /media/cdrom0[/FONT]
```any clues as to what is causing this?  The invisible partition should be /dev/hda6 as far as I can tell.  I was planning on using this machine for development and testing work stuff, but until I figure out whats up I am a little freaked out.

---

