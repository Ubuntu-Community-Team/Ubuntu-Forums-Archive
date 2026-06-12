---
title: "hard drive access"
date: 2006-07-28
forum: Desktop Environments
---

### Post by poingjam on 2006-07-28
I just installed Ubuntu.  I've got a second hard drive with Windows installed on it formatted NTFS, but whenever I try to browse it, it says I don't have the permissions to view the contents.  However, when I go to systems/administration/disks, and I go to change the access path, the browser displays all the files within it.  How do I enable it so I can actually view the contents of the drive?  The files aren't encrypted.

---

### Post by hw-tph on 2006-07-28
Try [this page](https://help.ubuntu.com/community/MountNtfsOnBoot) from the Wiki, and also [this one](https://help.ubuntu.com/community/MountingWindowsPartitions?action=show&redirect=NTFSReadWrite).


Håkan

---

### Post by poingjam on 2006-07-28
Alright, I've tried installing FUSE and NTFSprogs, but neither one wants to work.

For FUSE, I did ./configure and got:
configure: error: no acceptable C compiler found in $PATH
After a bunch of checking things.  Then I tried make and it said command not found.  So that's bad.

NTFSprogs gave me similar errors.  Apparently neither one installed.  I tried the other link that didn't involve either one, and it didn't work.  The drive is mounted, I just don't have the permissions to view it.  How do I get said permissions?

EDIT: I got them installed using Synaptic, I'm trying to get ntfsmount to work now.  Why is it that I can't seem to make a directory anywhere using the terminal, but it works fine through the GUI?  It keeps telling me "Permission denied" anytime I try mkdir in the terminal, anywhere at all.

EDIT AGAIN: ntfsmount isn't working.  It's telling me to use the force option to work a mounted filesystem.  I have no idea what that means.

---

