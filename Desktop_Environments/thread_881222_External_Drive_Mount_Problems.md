---
title: "External Drive Mount Problems"
date: 2008-08-05
forum: Desktop Environments
---

### Post by fhsm on 2008-08-05
**Problem**: I inadvertently set a bad mount point for an external firewire drive using the HH GUI.  The drive is now inaccessible.  Any attempt to umount & mount the drive / reboot etc returns the same error: “Attempts to mount the drive return "Cannot mount volume. Unable to mount volume" "mount_point cannot contain the following characters: newline, G_DIR_SEPERATOR (usually /)".”

**Status**: it looks like I've stumbled into a [[COLOR="SandyBrown"]known bug in HH[/COLOR]]("https://bugs.launchpad.net/ubuntu/+source/gnome-mount/+bug/107668").  I've figured out a workaround and [[COLOR="SandyBrown"]posted it in the known bug & workaround thread[/COLOR]]("http://ubuntuforums.org/showpost.php?p=5530231&postcount=44") of the forums.  My solution is far from perfect.  Although it lets me get to my drive the problem returns after a reboot and requires I rerun the workaround, which is:

*fdisk -l* to figure out what  device the drive is followed by *mount* with an explicit working mount point.  I know the drives UUID from *blkid* and I've had a look in */etc/fstab* but the external HD in question doesn't show up at all.

So I'm not really sure what to do next.  Can I just add a new line to the end of /etc/fstab?  If so what should that record look like?

Thanks.

---

### Post by tamoneya on 2008-08-05
here is the line for fstab```
UUID=<insert_UUID> /good/mountpoint ext3 defaults 0 0
```

---

### Post by fhsm on 2008-08-05
Thanks for the info on fstab.  I found that I was able to fix the origional problem.  A full writeup of the fix is posted in the [known bugs area]("http://ubuntuforums.org/showpost.php?p=5530231&postcount=44").

---

