---
title: "Desktop GUI for creating/mounting DMCrypt / LUKS containers"
date: 2010-07-22
forum: Desktop Environments
---

### Post by blueadept on 2010-07-22
Given the way nautilus handles encrypted volumes (entire partitions)... I'm really surprised that there's no GUI for formatting a drive (External disk or USB stick perhaps) in this way... 

Most Windows users are focussed on encrypted container files too, and we're really missing a trick here, because we have a great tool and a very high percentage of users are simply using Truecrypt instead becuase there's no GUI, and no practical way to use a container file without resorting to the command line.

If you do create a container file, and put a LUKS volume in it, then you CAN use it... as soon as it becomes visible as a loop device eg. "losetup -f container_file.luks" it is then visible to nautilus and you can use it like a partition... but there must be some logic in creating a GUI for managing cryptsetup... 

Thoughts?

---

