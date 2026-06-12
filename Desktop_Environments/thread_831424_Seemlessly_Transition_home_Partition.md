---
title: "Seemlessly Transition /home Partition?"
date: 2008-06-16
forum: Desktop Environments
---

### Post by swegner on 2008-06-16
Hi,

I'm helping my brother with his computer.  He's has a fairly standard Ubuntu setup, except his home directory is mounted on a separate hard-drive, formatted as JFS.  He's been having a lot of trouble accessing his files through Rhythmbox and other programs, and I think it is related to JFS.  So, I want to move him back to ext3.

My question is whether we can transition his files and home folder over seemlessly, without affecting the underlying Ubuntu installation.  Here are the steps as I see it:

[LIST]
[*]Boot from a LiveCD to run gparted
[*]Backup all files from his home partition onto his main partition (perhaps somewhere like /var/backup, to clean-up later)
[*]Unmount home partition, delete it, create new ext3 partition in its place
[*]Move all of the files back from /tmp directory (perhaps save the backup, just in case)
[*]Backup fstab and update with new partition info
[*]Reboot into Ubuntu, and hope for the best
[/LIST]
Will this work?  Are there any other references to the actual partition that will need to be updated?  Also, is there an automated way to update the fstab entries, or will this need to be done by hand?

---

### Post by sdennie on 2008-06-17
That sounds like the general idea, yes.  A couple of things:

1) Make sure to backup the files in a way that preserves their ownership and permissions.

2) Don't store anything in /tmp during this process.  Things stored in /tmp will likely be blasted on reboot.

3) Make sure you are storing the backup of the home directory somewhere that isn't on the LiveCD filesystem (this seems obvious but, I thought I'd point it out anyway).

Other than that, your plan sounds fine to me.

---

### Post by logos34 on 2008-06-17
like Vor says,

> 1) Make sure to backup the files in a way that preserves their ownership and permissions.

i.e.,

**sudo cp [COLOR="Red"]-a[/COLOR] **

Or use this as a guide:

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

