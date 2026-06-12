---
title: "I miss those panel apps (Mount)"
date: 2011-04-30
forum: Desktop Environments
---

### Post by Jeahavee on 2011-04-30
I need to easily or automatically mount my 2 partitions because one of them has all my music files on it. Before I just clicked mount on the panel app right click mount and then I could open Banshee or Rhythmbox and press play. Better yet how to I get to panel apps.

I can't easily mount the 2 partitions any other way. Warning I am being picky :P.

---

### Post by seeker901 on 2011-05-01
I agree.  I used the panel apps exclusively to mount my volumes.  Other than going to disk utility and mounting them that way, is there a quick and dirty way of doing it?

---

### Post by ankspo71 on 2011-05-01
Hi,
One way to mount partitions automatically is to use the "users" mount option in /etc/fstab. The "users" option means allow any ordinary user to mount the partition, and it will be done automatically on start up because "auto" is is already implied in the default mount options.

Here is an example showing my storage partitions in /etc/fstab. The mount options are shown in red.
```
# Storage
UUID=912d802c-631c-45ff-bb7d-b495d30e55a5 /media/sdb1 ext4 [COLOR="Red"]users[/COLOR] 0 0
UUID=7232a4f9-6a2e-46ad-be17-f05246e6729d /media/sdb2 ext4 [COLOR="Red"]users[/COLOR] 0 0
```

You can use these commands in the terminal to backup and edit your fstab
```
sudo cp /etc/fstab /etc/fstab-backup
gksudo gedit /etc/fstab
```

More information on fstab and mount options:
[https://help.ubuntu.com/community/AutomaticallyMountPartitions](https://help.ubuntu.com/community/AutomaticallyMountPartitions)
[http://linux.die.net/man/8/mount](http://linux.die.net/man/8/mount)
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
Hope this helps.

---

