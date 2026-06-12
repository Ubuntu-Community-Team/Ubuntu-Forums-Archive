---
title: "Nautilus will not stay in terminal"
date: 2011-08-16
forum: Desktop Environments
---

### Post by cculpepper on 2011-08-16
I am trying to create a script that takes a network resource off the network, and opens it in nautilus to recover files. Everything is working fine, except for the nautilus part. Nautilus opens just fine, but the script opens it and does not go on, even when nautilus is closed. when running another terminal instance with nautilus in it, when nautilus is closed, the extra terminal just sits there.

---

### Post by Morbius1 on 2011-08-16
I seriously doubt that this will help you since I don't know what kind of "network resource" you are accessing and I don't have much experience with scripting but I think the answer may be in not getting nautilus involved.

Let's say the network resource is a samba share.

Mount it locally by:
```
gvfs-mount smb://192.168.0.100/share-name
```Two things will happen:
[1] The remote share will be mounted automatically at:
> home/your-user-name/.gvfs/share-name on 192.168.0.100[2] You will get a mount icon on the desktop that will open up Nautilus if that's what you want to do.

You can change directories to the ".gvfs" directory in your script if you need to do something at that level.

When you no longer need the remote share unmount it:
```
gvfs-mount -u smb://192.168.0.100/share-name
```The mount point is released and the desktop icon will be removed.

---

### Post by cculpepper on 2011-08-17
I have a DRBD replicated drive. The script basically disconnects the replication, discovers the logical volume and mounts it to '/share'. It then opens up a nautilus window with 'nautilus /share'. The problem is that the script just stops there, unless i have 'xterm nautilus /share'. This opens up another terminal window and opens nautilus. the script only continues if I close out of the spawned terminal.

---

### Post by aeiah on 2011-08-17
this is flagged as xubuntu, so why not use thunar instead of nautilus?

also, are you launching with an ampersand, to send it to background so the script continues? eg:
```

nautilus /share &
```

perhaps its to do with how nautilus runs as a daemon. check the documentation i guess

---

### Post by cculpepper on 2011-08-17
I ran thunar instead, and the script worked as expected. This is my first foray into xubuntu so I assumed that that nautilus was the default file manager. Thanks for the help!

---

