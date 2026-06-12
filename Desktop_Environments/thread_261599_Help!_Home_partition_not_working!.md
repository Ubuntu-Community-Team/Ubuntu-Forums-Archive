---
title: "Help! Home partition not working!"
date: 2006-09-20
forum: Desktop Environments
---

### Post by alecjw on 2006-09-20
Here's my code in /etc/fstab to mount /home/.
```
/dev/hda5	/home		ext3	nodev,nosuid	0	4
```
What's wrong with it? It says, whenever I boot it up, that a filesystem has failed. I'm sure its because of that line because it happeed as soon as I added the line. If it's of any use, my / partition is hda1, Windoze partition is hda2 and the rest of the drive is a logical drive, hda3. In the logical drive are hda5 (home partition which won't mount) and hda6, 3GB of swap.

---

### Post by alecjw on 2006-09-21
Bump

---

### Post by Omnios on 2006-09-21
This is a link about fstab on tuxfiles.

[http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html)

they have an example of home as follows.

```

/dev/hdb1 		/home 		ext2 		defaults 		1 2

```

---

### Post by alecjw on 2006-09-21
Thanks! I though the 2 numbersat the end meant hard disk no, partition no.

---

