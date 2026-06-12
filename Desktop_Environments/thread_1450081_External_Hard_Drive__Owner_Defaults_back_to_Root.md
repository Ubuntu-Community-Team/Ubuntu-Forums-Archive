---
title: "External Hard Drive : Owner Defaults back to Root"
date: 2010-04-08
forum: Desktop Environments
---

### Post by doogiekd on 2010-04-08
Dear Friends, 

I have an external HD (1 TB WD Book) attached to my main Desktop. NTFS file format.

The problem: I am trying to share the entire drive and am receiving an error message that files are unable to be shared due to permissions (error 255) root is the owner.

I attempted to change the owner & file permissions on the drive using gksudo nautilus. Doing so is not allowed and it is changed to the root owner.

The same problem happens when I try to change owner of the external hard drive using sudo chmod.

I have also tried changing just specific files on the hard drive with the same resulting issue.

I want to be able to share the entire drive and contents with all users on the network, but can't because permission to do so is denied because the hard drive is owned by root.

Any solution to this problem?

Thanks.

---

### Post by coffeecat on 2010-04-08
The NTFS filesystem does not support Linux permissions so you cannot change ownership of files, folders or the whole drive by chmodding. When an NTFS partition is mounted using the ntfs-3g driver, all files and folders appear to be owned by root but ordinary users (on the host machine) can access all files read-write.

I guess that what you are encountering is a problem with samba - not a permissions problem on the NTFS drive per se - but I don't know enough about samba to say much more. It sounds as though setting up a NTFS partition directly as a samba share in a Linux machine is a non-starter, but I can suggest a way that may work around this.

On one machine, I use an internal NTFS partition as a data partition. In order to access this via a share, I created a symlink in a share in my home folder, linking to the partition. When viewed from another machine on the network, the data partition simply appeared as a folder within the share.

I don't know how elegantly this could be done with an external drive. If you are in the habit of having it mounted at bootup, then this should be fine, but I don't know whether the symlink will be problematic if you mount the drive after the desktop has loaded.

Anyway... perhaps something for you to experiment with.

---

### Post by soltanis on 2010-04-09
Go to a terminal and type:

```

id

```

The program will print out your user ID (uid) and group ID (gid) numbers. Remember what they are, then edit your /etc/fstab line which you mount the drive under so that it looks like this:

```

# in /etc/fstab
# I am pretending that /dev/sdb1 is your NTFS partition and that
# /media/mount is where it is mounted. Change according to your system.
# ** Replace <UID> and <GID> with your uid and gid from the id command

/dev/sdb1    /media/mount    ntfs-3g    uid=<UID>,gid=<GID>    0 0

```

You can also mount it like this, as root:

```

sudo mount -t ntfs-3g /dev/sdb1 /media/mount -o uid=<UID>,gid=<GID>

```

In general, when the uid and gid options are present the module will mount the filesystem giving ownership to that user and group. It defaults to the uid and gid of the calling process, but since you normally run mount as root, that means it gives ownership to root.

Filesystems not supporting permissions, like NTFS, normally default to permissions of 0777, meaning anyone can read, write, and execute, so I find it odd that Samba is doing that to you, although it wouldn't be the first time someone's written a program that does something stupid.

---

