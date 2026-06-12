---
title: "Argh! Cant mount Windows partition!"
date: 2009-02-13
forum: General Help
---

### Post by Bloaergh on 2009-02-13
Evening Ubuntu forums, FNG here. Ive been a windows user my entire life and Im just now trying to leave (join?) the cult.

Ive got Intrepid ibex dual booted on my laptop here with Windows Vista. Im trying to access the windows partition from within Ubuntu. Im fairly sure that i'm almost there- Google has been my mentor so far.

The last issue i'm having is actually mounting the volume. When I use:
sudo mount /media/Windows

I get an error in the terminal, reading:
fuse: mount failed: Device or resource busy.

Does anyone know what could be causing this? I feel so very close, and yet so far away :(

---

### Post by michael1384 on 2009-02-13
Was there an unclean shutdown last time you used Windows?

---

### Post by Bloaergh on 2009-02-13
> **michael1384 said:**
> Was there an unclean shutdown last time you used Windows?

Nope, shutdown was clean.

---

### Post by drs305 on 2009-02-13
If there aren't disk errors you can also get that message if the device is already mounted (perhaps to another mount point). You can run this to see what partitions are currently mounted:
```

mount | grep "/dev/sd"

```

If you don't have it listed in fstab already, the simple way to do so is to install ntfs-config and then run it via System Tools > NTFS Configuration Tool. It will ask for a mount point, the name you select will be put in /media if it doesn't already exist, and the app will add the entry to fstab.

To install it (and ntfsprogs, a small collection of ntfs tools): 
```

sudo apt-get install ntfs-config ntfsprogs

```

---

### Post by personjerry on 2009-02-13
open gparted (type gparted in a terminal window or go to System -> Administration -> Partition Editor) and find your partition, and see what's wrong with it.

---

