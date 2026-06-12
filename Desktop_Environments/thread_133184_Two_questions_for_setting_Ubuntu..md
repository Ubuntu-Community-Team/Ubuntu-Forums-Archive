---
title: "Two questions for setting Ubuntu."
date: 2006-02-19
forum: Desktop Environments
---

### Post by joelomar on 2006-02-19
I have two questions regarding the set up of an Ubuntu workstation.

First I find the Ubuntu partitioner confusing.  Say I have a 20 GB hard drive and I want /home on a separate partition, I don't care how the other partitions end up.  I tried partitioning using the installation tool but I haven't had much success.  Can anyone point me or give me step by step instructions for doing it?

Also once Ubuntu is up and running properly, how can I set up various folders within the same box to be shared between different users?  I know it has to be done with permissions, and I want to keep the use of symbolic links to a minimum.  These two users must be authorized the same rights to these folders (mostly pictures and music).

Thanks!  Any info is appreciated.

---

### Post by bluevoodoo1 on 2006-02-19
For a separate home partition, try this link... [http://users.bigpond.net.au/hermanzone/p14.htm](http://users.bigpond.net.au/hermanzone/p14.htm)

You can use the command chmod to change permissions, I believe chmod 744 will let the owner read/write/execute and only let the others read, 755 should let the others read and execute, but not write. Or, you can use Nautilus, right click on the folder or file you want and you can graphically change permissions.

EDIT: typos

---

### Post by joelomar on 2006-02-19
Would a suggestion be to place this folder on the root /home folder, accesible to all users?

---

### Post by astoltz on 2006-02-19
I made two directories:  /usr/share/music and /usr/share/pictures/.  Then I made a new group called 'media' and changed the group of music/ and pictures/ (and all the files) to media.  The permissions I made 775 so owner and group have full access but everyone else has read-only.  Now who ever should have access to the directories need only be a member of the group 'media'.  

This works great for us - the wife and I are in media but the kids can still see the pictures and play the music without fear of deleting something they shouldn't.

---

