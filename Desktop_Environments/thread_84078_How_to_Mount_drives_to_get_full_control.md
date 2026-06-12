---
title: "How to Mount drives to get full control"
date: 2005-10-30
forum: Desktop Environments
---

### Post by DominYk on 2005-10-30
Hi there!
I'm a fresh new Linux user.
I'm trying to mount a VFAT partition in Ubuntu that can let me write in with Evolution.
I mean... this is an extract from my FSTAB:

/dev/mapper/pdc_bgaafcedce1	/media/Dati	vfat		defaults,umask=0000		0	0

The owner of the disk is root.
I would like to let Evolution write in there (I've made a symbolic link to a folder of this disk) but it told me that he cannot set the lock on a mailbox file.

As I can see the owner of the mailbox file is Root, like every other file or folders with 777 permisions.

I've tried CHOWN but I get "Operation not permitted" (even with SUDO)

How can I prevent this and have a situation like "everyone -> full control" in Windows?

The symbolic link was made this way:
[email]dominyk@home:~/.evol[/email]ution$ ln /media/Dati/Mimino/Posta/evolution/mail -s

Is this the correct way?

Thanks for every info!

DominYk

---

### Post by DominYk on 2005-10-31
Hi all.

Problem solved... at least for mounting drives.

Let me Explain...

What I was trying to do was to have the Evolution data files on another disk which is mirrored, for security reason.

The mirrored disk is partitioned with FAT file system, because it is used to store personal information even with Windows.

The problem was not in the symbolic link nor with the FSTAB parameters but in the fact that Evolution (at least it seems to me...) is not able to work on FAT partitions just because it has to set locks on files, operation not possible on FAT partitions.

So... if there is someone that can help with this strange behaviour... let me know!

Thanks everybody.

DominYk

---

