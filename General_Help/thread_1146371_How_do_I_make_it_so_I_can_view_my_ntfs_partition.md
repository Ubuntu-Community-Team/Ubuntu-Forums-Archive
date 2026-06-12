---
title: "How do I make it so I can view my ntfs partition?"
date: 2009-05-02
forum: General Help
---

### Post by CynicalPsycho on 2009-05-02
I'm dual booting ubuntu and win vista.
How do I make my ntfs (windows) partition readable in linux?
and to expand on that, how do I make an ntfs flashdrive readable on ubuntu?

---

### Post by codeseer on 2009-05-02
> **CynicalPsycho said:**
> I'm dual booting ubuntu and win vista.
How do I make my ntfs (windows) partition readable in linux?
and to expand on that, how do I make an ntfs flashdrive readable on ubuntu?

Run this:

```

sudo blkid

```

Note the UUID for the drive you want to mount.

Create a folder to mount the drive to:

```

sudo mkdir /media/PickAName

```

```

gksudo gedit /etc/fstab

```

You'll be inserting something that looks like this then:

```

# /dev/sdb1 - 320 GB Storage
UUID=TheUUIDFromBlkid    /media/TheMountPointYouCreated    ntfs    users,defaults,umask=000    0    0

```

Use the TAB key to separate columns in this file to avoid issues.

Edit:

Your ntfs usb flash drive isn't automatically readable? Check the Places menu.

---

### Post by Paqman on 2009-05-02
Simple solution: [NTFS Config]("apt:ntfs-config") (click to install straight from the repos).

It's a GUI that will get your NTFS partition mounted in a snap.

---

### Post by codeseer on 2009-05-02
> **Paqman said:**
> Simple solution: [NTFS Config]("apt:ntfs-config") (click to install straight from the repos).

It's a GUI that will get your NTFS partition mounted in a snap.

I like it HARD!!! :guitar:

Nah, I've just never tried that out, so I don't recommend it to people; I'll give it a go in my VirtualBox and have a look.

---

### Post by codeseer on 2009-05-02
Yeah, that works pretty well. I'd like it to have an interface for removing entries as well though.

Notes:

When you enter the mount point, it only wants the name, not the entire path. It mounts under /media, given the name you supply.

---

### Post by CynicalPsycho on 2009-05-02
> **codeseer said:**
> Run this:

```

sudo blkid

```

Note the UUID for the drive you want to mount.

Create a folder to mount the drive to:

```

sudo mkdir /media/PickAName

```

```

gksudo gedit /etc/fstab

```

You'll be inserting something that looks like this then:

```

# /dev/sdb1 - 320 GB Storage
UUID=TheUUIDFromBlkid    /media/TheMountPointYouCreated    ntfs    users,defaults,umask=000    0    0

```

Use the TAB key to separate columns in this file to avoid issues.

Edit:

Your ntfs usb flash drive isn't automatically readable? Check the Places menu.

that was friggan beautiful... thanks!

---

