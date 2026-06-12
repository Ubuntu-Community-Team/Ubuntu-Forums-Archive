---
title: "trouble with permissions of a /home directory mounted off a partition"
date: 2008-12-27
forum: General Help
---

### Post by wmdiem on 2008-12-27
I have installed ubuntu (8.04) on a friend's computer. I set it up as a dual boot with xp. Ubuntu is residing on a tiny partition. I then setup fstab to mount the ntfs partion. I then moved the /home directory onto the ntfs partition and put an entry in fstab to bind it to /home.
The problem is that now i get errors at bootup because the user's home directory is owned by root and not by the user. 
I was thinking there might be a parameter I could change in the fstab entry to have the home directory load as hers not at the root's. The problem with this seems to be that if I forced the /home to belong to her,then other users (if there were others) would then have the same problem. 
Is there any way to just change the owner of the one directory (a subdirectory of a bound directory?)
Many thanks in advance.

---

### Post by wmdiem on 2008-12-27
I should also note that when I run 
sudo chown -Rv username:users /home/username
It lists the contents and says it is changing the ownership, but when I run ls -al it still shows the old ownership, root:plugdev

---

### Post by wmdiem on 2008-12-27
anyone? this should be so simple and I really can't find anything on it. it seems like sudo chown should do it, and it looks like it does, but once it's done nothing has changed.
Please help, I don't want to leave a new linux convert with a half-working system.

---

### Post by caljohnsmith on 2008-12-27
Unfortunately you can't have the entire home directory on an NTFS partition, because NTFS file systems do not keep Linux ownership/permissions data. You could instead keep /home on his main Ubuntu partition, but instead move the "Documents", "Music", "Videos", etc folders to the NTFS partition, and then simply use a symbolic link to link those directories back to your friend's /home/username directory. You could do something like:
```
ln -s /path_to_documents_partition/Videos ~/.
```
And that will link the "Videos" folder on the NTFS partition back to the /home/username directory. How about giving that a shot and let me know how it goes.

---

### Post by wmdiem on 2008-12-27
Thanks, the error is gone. 
I wish there were a way to just asign the ownership and permissions when you bind a folder off an NTFS system and then have the setting just get inherited down. (I also of course wish chown would throw an error instead of saying it had changed the owner of directories it can't change)
But such is life. 
Thanks a lot for the help.

---

