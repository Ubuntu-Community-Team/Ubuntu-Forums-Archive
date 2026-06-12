---
title: "How to get rid of unwanted icons on the desktop"
date: 2008-02-13
forum: Desktop Effects &amp; Customization
---

### Post by zeiz on 2008-02-13
Hi everybody!
I just read a thread marked [SOLVED] "Remove Icons from Desktop" (2 weeks ago) and I don't think it was really solved. So I'd like to share my experience with the community. 
I had the same problem: my slave drive has 3 partitions with abandoned XP + some pro apps so all 3 partitions appeared on my desktop. I set spindown for my slave drive to 0 because I use that drive very seldom but those icons were like reminders that I still have Windows.
I googled and found the following: ALT-F2, type gconf-editor, navigate to Nautilus, then to Desktop and then clear visibility check box. That was most valuable advice I could find on Internet. That's great of course but this just hides icons and doesn't unmount partitions. Of course after every logon I could  unmount them from terminal with sudo, but that's not a solution. I'm a newbie and I only understood that it must be a file where those partitions are mounted by default and even if I forcedly unmount them for a session they appear again on next logon. This file is fstab in /etc folder. It looked like this:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=57e8c61d-221b-452d-9fc6-62574c266c1d /               ext3    defaults,errors=remount-ro 0       1
# /dev/sdb1
UUID=7047-EF66  /media/sdb1     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sdb5
UUID=6054C71254C6E9BC /media/sdb5     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sdb6
UUID=8841-D9FD  /media/sdb6     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda6
UUID=4afc3c98-39a8-424b-8e78-cd6cc8ead550 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0

The nasty partitions are sdb1, sdb5 and sdb6. On the other hand I can mount (with user password) and umount my docs partition on my master drive. Its icon appears on my desktop when the partition is mounted and disappears after umounting. For me it is very convenient. In the thread above was an advice to mount on /mnt that is not quite right because all the files from mounted partion appear under /mount and if you mount something else there...it could be a trouble. It's necessary at least to create a folder /mnt/mypartition. Anyway in this case an icon doesn't appear on the desktop after mounting and then it's possible to forget to unmount the partition (and a floppy :( ).
So I backup fstab to fstab.bak and then put comments on those partitions' entries. 
Now fstab looks like this:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=57e8c61d-221b-452d-9fc6-62574c266c1d /               ext3    defaults,errors=remount-ro 0       1
# /dev/sdb1
#UUID=7047-EF66  /media/sdb1     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sdb5
#UUID=6054C71254C6E9BC /media/sdb5     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sdb6
#UUID=8841-D9FD  /media/sdb6     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda6
UUID=4afc3c98-39a8-424b-8e78-cd6cc8ead550 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0

I can now mount and unmount any partition having its icon on the desktop only when it's mounted. Also I'm not loosing icons when I'm inserting cd/dvd, usb flash or floppy; Actually now mounted partition appears as disk, disk1, disk2 that is not quite convenient if a few partitions mounted. I tried (and it works) to put emblems on each icon (right click on an icon>Properties>Emblems. What is interesting that smart Ubuntu remembers my emblems and they appear again (correctly!) after remounting and after reboot. Hopefully this "howto" could be useful for newbies like myself :)

---

### Post by adi_das on 2008-02-13
Right click on the desktop and select clean up by name

---

### Post by zeiz on 2008-02-13
Great, thank you! This is much easier and faster than work with gconf-editor.:) 
However I believe that it will not actually unmount partitions but only hide icons.
My main target was to unmount unused partitions and shutdown slave drive. Can somebody see now those my partitions?

---

