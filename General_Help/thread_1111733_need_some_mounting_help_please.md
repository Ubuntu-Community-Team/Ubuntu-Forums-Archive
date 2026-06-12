---
title: "need some mounting help please"
date: 2009-03-30
forum: General Help
---

### Post by tweeks on 2009-03-30
i just put ubuntu 8.04 on eee pc 1000H, wasn't sure about the partitioning so just went with one the automatic options.  df shows like this:

Filesystem           1K-blocks      Used Available Use% Mounted on

/dev/sda1              7435056   2721264   4339080  39% /
varrun                  513472       100    513372   1% /var/run
varlock                 513472         0    513472   0% /var/lock
udev                    513472        56    513416   1% /dev
devshm                  513472        24    513448   1% /dev/shm

The main soldid state drive (28gb) is not is /etc/fstab, so I added:

/dev/sdb1   /home     usr,auto,       ext3  rw    0     0

when i ran the command: sudo mount /dev/sdb1  /home  it put all the folders that were in /  into my /home/user  after about an hour of trying to figure how to get it back to the way it was, I now have it back to where all the normal folders, Documents, Desktop, etc. are back in my 
/home/user directory so i'm back to square one.  any help  would be greatly appreciated on how to get the /home/user folders to mount on my 28gb partition 
thanks,
tim

---

### Post by zvacet on 2009-03-31
Are you trying to make separate home partition? If you do look [this]("http://www.ivankuznetsov.com/2008/04/moving-home-to-its-own-partition.html") guide.

---

