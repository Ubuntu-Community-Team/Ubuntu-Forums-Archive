---
title: "Read Only Problem"
date: 2018-09-10
forum: Gaming &amp; Leisure
---

### Post by spagbr0 on 2018-09-10
I'm new to linux and am using Lubuntu, also, not too sure if this is the right place to post this. 
I have 2 drives on my pc, and before I switched to linux both were Read-Write, but now that I'm on linux, my games drive has been switched to read only.
I managed to get it to the point where I can edit the folders manually but whenever I try to link my games drive with steam it gives me a pop up saying "Failed to create a folder, this drive is read only"
Any help would be appreciated

---

### Post by TheFu on 2018-09-10
When storage is about to fail, one of the ways it is protected by Linux is the mount is changed to read-only.  So the first thing you should do is make a backup of anything you don't want to loose.

In the meantime, the output from **df -hT** would be helpful too. When you post it, please use *code tags* so things line up correctly and it is readable. If it doesn't look the same posted here as inside a terminal, then you didn't do it correctly.

---

### Post by spagbr0 on 2018-09-10
Not too sure what code tags are, but on my end it looks about right when I paste this:

Not too sure what code tags are, but I played around with the spacing for a bit to make it read like in the terminal.

```
Filesystem     Type      Size  Used   Avail Use%  Mounted on
udev        devtmpfs      12G        0    12G   0%     /dev
tmpfs             tmpfs     2.4G  1.4M   2.4G   1%     /run
/dev/sda2        ext4      2.7T  8.6G    2.6T   1%     /
tmpfs             tmpfs      12G   73M    12G   1%     /dev/shm
tmpfs             tmpfs     5.0M  4.0K    5.0M   1%    /run/lock
tmpfs             tmpfs      12G       0      12G   0%    /sys/fs/cgroup
tmpfs             tmpfs     2.4G   24K     2.4G   1%    /run/user/1000
/dev/sdb5    fuseblk   932G  462G    470G  50%  /media/lucas/9646C63F46C61FBB
/dev/sdc1          vfat     29G   1.1G      28G   4%   /media/lucas/LUBUNTU 18
```

---

### Post by QIII on 2018-09-10
I added code tags.  As you will note, the formatting is now incorrect because you reformatted the plain text.

Please use code tags.

---

### Post by spagbr0 on 2018-09-11
Thanks for showing me how that works.


```
Filesystem     Type      Size  Used Avail Use% Mounted on
udev           devtmpfs   12G     0   12G   0% /dev
tmpfs          tmpfs     2.4G  1.4M  2.4G   1% /run
/dev/sda2      ext4      2.7T  8.6G  2.6T   1% /
tmpfs          tmpfs      12G  4.0M   12G   1% /dev/shm
tmpfs          tmpfs     5.0M  4.0K  5.0M   1% /run/lock
tmpfs          tmpfs      12G     0   12G   0% /sys/fs/cgroup
tmpfs          tmpfs     2.4G   20K  2.4G   1% /run/user/1000
/dev/sdc1      vfat       29G  1.1G   28G   4% /media/lucas/LUBUNTU 18_
```

Hope this helps.

---

### Post by TheFu on 2018-09-11
```
/dev/sdc1      vfat       29G  1.1G   28G   4% /media/lucas/LUBUNTU 18_
```
Is that the problem storage or is it one of the others?

Was there anything in the system logs showing errors or warnings?

Completely unrelated, but having the OS on a huge partition like this system does can cause issues.  Generally, I limit the / partition to 25G and put any other storage needed into other partitions.  

Why?  Backups are generally performed at the partition level and backing up the OS is a different need than backing up end-user or media files.  It is pretty easy to backup 25G, but not nearly as easy to backup 2TB.  I also like to keep media files separate, since they don't change very often and don't need backups nearly as often as the OS or documents and email in my HOME which change all the time.

---

### Post by spagbr0 on 2018-09-11
I think at this point it might be an actual mechanical or electrical issue with the drive as nothing I've tried has fixed it, at least none of the common fixes.
The drive didn't show up on the df -hT so I think it might be broken.
Thanks for the assistance though :)

---

### Post by oldrocker99 on 2018-09-13
Here's one way to make your drive read-write. Use chmod:

[https://askubuntu.com/questions/90339/how-do-i-set-read-write-permissions-my-hard-drives](https://askubuntu.com/questions/90339/how-do-i-set-read-write-permissions-my-hard-drives)

The Fu above wrote a true fact, but it's likely that the owner is root. Change ownership with chmod.

An easier way is to use the file manager. Most file managers can change permissions, it you run them thus:
```
sudo file.manager.name
```

I mean Nautilus, Caja, and other file managers. If you run it as root, you can click on a file, folder, or whole drive and right-click to Properties. Then you can change ownership to yourself, and set read-write flags on files and folders.

It might be a good idea to backup all files on your NTFS drives, reformat the drive with the Linux ext4 format, which is far less error-creating than NTFS. Then just copy the files to the newly-formatted drive. I had a nasty experience with a dual-formatted drive, and, while the Linux partition  worked fine, the NTFS partition gave up the ghost.

Just sayin'(:P.

---

### Post by TheFu on 2018-09-13
chmod doesn't work on vfat or NTFS file systems.  For those file systems, permissions are completely controlled by mount options.

Unless a detailed NTFS-Unix mapping is undertaken and enabled.  I've never done this, but have used it about 20 yrs ago.

Also, be extremely careful even running any GUI tools as with sudo. Even without directly modifying any files, it can change permissions and set ownership that isn't intended.

---

### Post by oldrocker99 on 2018-09-14
All this is true. The best advice I could give is to do a backup of the NTFS drives, and then format to ext4. NTFS is an inferior filesystem, IMHO.

---

