---
title: "kde auto unmount disks upon exit??"
date: 2007-03-10
forum: Desktop Environments
---

### Post by polomint on 2007-03-10
Hi!  first post here...

been using ubuntu for a few weeks now and so far im loving it :) !

however, i've notice a strange problem (or a feature?) with kde; whenever I log out, all my drives get automatically unmounted.  Nothing major, but it just means that every time I log in, I have to do a 'sudo mount -a' to get all my drives back, which is a bit of a nuisance ...  Gnome never did this. 

is there a way to tell kde to stop automatically unmount drives after log out? I've been looking  for an option in kcontrol but there doesn't seem to be one...

any help is appreciated!!

(btw the drives in question are windows NTFS partitions)

---

### Post by ewankho on 2007-03-11
Maybe you can auto mount it when starting up. In KDE System Setting->Disk & Files modify the partition you want to mount. Click on 'Enable at Start Up'.

---

### Post by polomint on 2007-03-11
Thanks but i've already tried that but it doesn't seem work. I think the 'Enable at Start Up' means system startup, not kde startup. 

It's probably to do with the mount points inside /media that's causing the problems. also i've noticed that the partitions are named with some weird UUID's instead of /dev/sda1 etc. I'll try to mount the partitions at different mount points to see if it helps.

---

### Post by Charles Hand on 2007-03-24
I'm having the same problem. Is this a feature or a bug. If a feature, can it be turned off?

I suppose if KDE is going to insist on unmounting everything in /media, I could mount my drives somplace else, like /mnt. But then I have a lot of pointers to /media/xxx that would have to be changed.

(rant)
I hate magic directory names where the rules are based on the name of the directory. Magic directory names are one reason I don't run Windows.

---

### Post by polomint on 2007-03-30
Hi, the problem seems to go away after changing the mount points elsewhere via fstab file. 
but, they will no longer appears on desktops as icons ... 

i think it is a feature rather than a bug, but still it's annoying not to have an option to disable this 'feature'. 

indeed, rules based on directories can be of a nusance. normally only root can use mount commands, but apparantly if a partition is mounted in /media, any user can umount it by issuing the command 'pumount /media/[name]', provided certain policies are met (whatever that means ).   'man pmount' gives a lot of information!

---

