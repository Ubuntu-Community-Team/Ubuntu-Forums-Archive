---
title: "profile restoration script and gvfs permissions"
date: 2011-02-19
forum: Desktop Environments
---

### Post by jlittle on 2011-02-19
I am having a problem with a script I am developing to restore a profile from a snapshot.  It is part of a deployment  strategy for patron computers at our county library. Every night I run  the script to restore the "guest" account from a a preset snapshot.  Basically this is what the script does: 

1 Kill the guest login session if logged in 
2 Copy Firefox places.sqlite to backup # preserve for audit trail 
3 Remove /.backup/guest.Backup  # previous CYA copy of guest account 
4 Move /home/guest to /.backup/guest.Backup # New CYA backup of guest 
5 Un tar snapshot of guest to /home/guest 
6 Copy saved Firefox places.sqlite from step 2 to guest account 

The problem I am having is I am getting an error: 

rm: cannot remove `/.backup/guest.Backup/.gvfs': Is a directory 

What is the best approach here. I wouldn't think killing the gvfs-fuse-daemon is the solution. I think I just want to temporarily disable it to the restore and prevent the error being generated. I want to get this script ironed out, because I want to deploy this on  about 15 workstations.

-- 
Jonathan

---

### Post by jlittle on 2011-04-16
To answer my own question for anyone in a similar situation you just have to umount the .gvfs as that user, in this case "guest", before moving|deleting|whatever the guest profile and then remount it afterward.

# unmount the .gvfs
sudo -u guest sh -c "fusermount -uz /home/guest/.gvfs"
...
# backup, restore or whatever your scripts does with "guest" profile
...
 # now remount it
sudo -u guest sh -c "/usr/lib/gvfs/gvfs-fuse-daemon /home/guest/.gvfs"

-- 
Jonathan

---

