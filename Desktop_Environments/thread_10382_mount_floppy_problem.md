---
title: "mount floppy problem"
date: 2005-01-07
forum: Desktop Environments
---

### Post by redbricks on 2005-01-07
hi at all the list
i'm new about ubuntu and used only some months debian and about 1 year playing with mandrake
so you know how newbie i am
got this problem: when i try to mount my floppy disk got this message
"mount: i could not determine the fs type and none was specified"
googlin i found this tip: edit modules and add floppy then reboot 
it worked ok for one floppy disk but the other got the same problem
in modules floppy now exist
tried also modprobe, mount -t vfat and all the commands i know
what can i do?

oops...kernel k7 on amd athlon xp2400

thanx

---

### Post by ulrich on 2005-01-07
after adding floppy to modules did you
```

sudo update-modules

```

?

---

### Post by redbricks on 2005-01-08
[QUOTE=][/QUOTE]
 tried also update modules but the disk cannot be mounted and the message is the same posted over
thanx

now i'll try another googling and look well at modules man and gnome user guide (for mount devices and so on)

---

### Post by istoyanov on 2005-01-08
I have exactly the same problem with some floppy disks, but not with others. I noticed that when I have formatted such unreadable floppies via the disk formatter utulity these become readable (i.e. I can mount/unmount read/write them successfully).

---

