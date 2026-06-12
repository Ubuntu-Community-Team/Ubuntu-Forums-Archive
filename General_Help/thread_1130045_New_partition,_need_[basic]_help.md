---
title: "New partition, need [basic] help"
date: 2009-04-19
forum: General Help
---

### Post by Xero Xenith on 2009-04-19
Hey guys, this is my setup at the moment.

**_DRIVE 1 (SATA) - OS DRIVE_**
*[a few different OS's on a few partitions, all set up and working]*
--Empty 100 GB ext3 partition, aka **sda3**

**_DRIVE 2 (SATA) - DATA/HOME DRIVE_**
--just one 500 GB partition, used as /home.

My problem is, my 500 GB home drive is almost full. I'd like to relocate some of it, like my music and photos perhaps, onto the 100 GB of empty space on my OS drive.
The partition is already made, but it's not mounted when I boot, and I'm guessing I'd need to sort out some permissions first, before moving the files and making folder links.

I'm well versed in folder linking already, it's just this other stuff I'm sort of lost with.

Thanks to anyone who can lend a hand :)

---

### Post by codeseer on 2009-04-19
So, you want the 100 GB partition to be mounted upon boot?

Open a terminal and type this:

```

blkid

gksudo gedit /etc/fstab

```

Put this line in /etc/fstab. Take the UUID listed from 'blkid' and place it in the proper area as well as putting your own name for the mount.

```

# **MOUNTNAMEHERE**
UUID=**UUIDHERE**	/media/**MOUNTNAMEHERE**	ext3		rw,nosuid,nodev,errors=continue,data=ordered	0	1

```

---

### Post by Xero Xenith on 2009-04-19
Yes, but I don't know if there's anything else I need to do, to make sure it's all going to play nice. Just being cautious here... :)

---

### Post by codeseer on 2009-04-19
That should get you set up. You can then just copy the files over.

---

### Post by Xero Xenith on 2009-04-19
Thanks a lot! :) I'll give it a shot.

[size=1]Hehe, that rhymes =D[/size]

late edit: just confirming that it did work perfectly in both Kubuntu and Ubuntu. Thanks :D

even later: note for me, this is what I want. Also an example for anyone looking :)
```
# /dev/sda3
UUID=5d9186fc-2995-4edb-b8af-0444e17dc5a0	/media/extra	ext3		rw,nosuid,nodev,errors=continue,data=ordered	0	1
```

---

