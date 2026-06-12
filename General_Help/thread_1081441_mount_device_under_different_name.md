---
title: "mount device under different name"
date: 2009-02-26
forum: General Help
---

### Post by evaristegalois on 2009-02-26
I have a device (a CF card reader) that automatically mounts at

/media/NEW VOLUME

when I plug it in. I'd rather have it mounted somewhere else under a different name, e.g. /home/myname/cfcard. How do I do this, and, ideally, how do I do it on the command line or, better yet, automatically when I plug in the device?

Thanks for helping.

---

### Post by ajgreeny on 2009-02-26
You could use gparted to label the device/partition.  Install it and then go to System>Administration>Partition Editor if you don't already have it.  Make sure the device is unmounted before you work on it in gparted.

---

### Post by Slim Odds on 2009-02-26
> **ajgreeny said:**
> You could use gparted to label the device/partition.  Install it and then go to System>Administration>Partition Editor if you don't already have it.  Make sure the device is unmounted before you work on it in gparted.

It will still be mounted under /media

This is the place where Ubuntu puts dynamic devices.

---

### Post by phr33k-dc on 2009-02-26
What should you label it as in gparted? lets say if you wanted to move it to for example 'Home Foldeer'

---

### Post by dcstar on 2009-02-27
> **phr33k-dc said:**
> What should you label it as in gparted? lets say if you wanted to move it to for example 'Home Foldeer'

All removable media will be mounted under /media - that is a Linux standard.

You are free to make links to mounted media in there and put them anywhere you like:

```
gksudo nautilus
```

---

