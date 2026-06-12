---
title: "Mount/Unmount script?"
date: 2009-01-01
forum: General Help
---

### Post by Dthorton15 on 2009-01-01
Hello!

I have a Western Digital External HD that keeps constantly spinning while its plugged into my server(when its running, which is always.)

Basically I only use it for backups and the software that I use to do my backups (webmin*shreeks*) allows me to run a command before and after the back up. So I was looking for a way to mount the HD before the backup then unmount it so it went dormant immediately after the backup.

Can anyone shed some light on how I should do this?

---

### Post by bodhi.zazen on 2009-01-01
You do not need a script.

First make a mount point

```
sudo mkdir /media/backup
```

Then you can mount the drive with

```
sudo mount UUID=xxx.yyy.zzz /media/backup
```

and unmount with 

```
sudo umount /media/backup
```

To see your uuid :

```
sudo blkid
```

You can also add an entry to fstab

[How to fstab - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?&t=283131")

---

### Post by jerome1232 on 2009-01-01
If you create an fstab entry that has the user or users option in it then regular users can mount/unmount the volume. This would make it so that your script wouldn't have to run at boot.

Also if you give it the noauto option it will not be automatically mounted at boot.

an example fstab for a ext3 drive, just give that link bodhi.zazen gave you a good read over, it gives alot of detail.

```
UUID=xxxx-xxx-xxxx-xxxx /mnt/point ext3 noauto,users 0 0
```

Then you can run those mount/umount commands as a regular user from this backup program you use.

---

### Post by Dthorton15 on 2009-01-07
ok so my commands would look like this

this is waht i have in my fstab```
/dev/sdc1  /backup  vfat  suid,uid=0,dev,exec  0  0

```
Before - to load the HD I would use
```
sudo mount sdc1 /media/backup
```now I want it to wait like 30 seconds so the hd can start spinning and do w.e it wants so could  I
```
sudo mount sdc1 /media/backup;wait 30
``` or something like that

and to unmount```
sudo unmount /backup
```and then i want it to restart after the backup so
```
sudo unmount sdc1 /media/backup;reboot
```

---

### Post by HermanAB on 2009-01-07
No, unmounting is the wrong solution to this problem.  Rather use hdparm and set the drive to spin down and go to sleep after a period of inactivity without unmounting it.

Read 'man hdparm' and put the command at the end of /etc/rc.d/rc.local.  The drive will then spin down/up all by itself when required.

Cheers,

Herman

---

