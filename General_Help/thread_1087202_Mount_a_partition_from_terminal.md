---
title: "Mount a partition from terminal"
date: 2009-03-04
forum: General Help
---

### Post by sjmacewan on 2009-03-04
Hey all,
So, don't ask why but I currently have a separate partition with all of my music on it. Accessing the files is as easy as clicking on the link to the partition in the Places tab in Nautlius. However, this means that everytime I want to listen to my music, I need to open a file browser and click that link to get it to mount the partition.
I was thinking that I could replace my Amarok opening command in my panel to include a call to mount the partition, THEN open Amarok.
Problem: I'm not entirely sure what's being done behind the scenes when I click the link in the Nautilus browser to mount the partition.

Any tips?

Let me know if none of that made any sense.

Also, I DON'T want to just have the partition automatically mounted on startup if I don't have to.

---

### Post by hexanol on 2009-03-04
Well, open a console window (i.e. terminal) and just after clicking the link to your partition/file system where your music is stored, enter

```
$ mount | tail -n1
```

This will show the last file system mounted (i.e. the one who holds your music). Now, if you want to mount this file system before launching amarok, you'll need some kind of small script who looks if the file system is already mounted, and if not, mounts it.

You should add a line to /etc/fstab so you can easily mount and unmount this file system. If you don't want it to mount automatically at startup, you just need to add the "noauto" option and it will mount the file system only when told explicitly (i.e. "mount /dev/sdXY")

---

### Post by sjmacewan on 2009-03-04
Great! I just didn't know how to find out which sda# it was.

In case anyone else is doing the same thing and happens upon this post, here's my script:

```

#!/bin/bash

# part: mounted location of media partition
part=/media/disk
cmd=$(mount | grep $part | cut -d\  -f3)

if [ "$cmd" != "$part" ]
then
	mount /dev/sda1
	amarok
else
	amarok
fi
exit 0


```

Where /dev/sda1 should be replaced by your partition of interest, and amarok could be replaced by whatever you wish to open upon mounting

Thanks again

---

### Post by hexanol on 2009-03-04
You're welcome! :)

---

