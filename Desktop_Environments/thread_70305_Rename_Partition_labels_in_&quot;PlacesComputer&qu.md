---
title: "Rename Partition labels in &quot;Places\Computer&quot;"
date: 2005-09-29
forum: Desktop Environments
---

### Post by aaron321ca on 2005-09-29
Hi there, 
I would like to rename the partitions listed under Places\Computer to something more descriptive than hda1, hda2, etc.  Unfortunately, I have been unable to find the solution to my problem.  
As suggested by one of the threads, I created partition labels using the "e2label" command.  So for instance, my /dev/hda7 partition had a label called "docs".  However, this label does not show up under Places\Computer.  
Does such a solution exist?  
Thanks in advance.

---

### Post by SilentCacophony on 2005-09-29
I was vexed by the same problem, and found a solution that worked for me. Unfortunately, I still don't know much about how Ubuntu sets up the Places/Computer, so there may be some other ramifications I haven't noticed...

Anyway, the way that worked for me:  Say, you have a second HD mounted as *hdb1*, and you want to change it to *share*:
I logged out of ubuntu (to the gdm prompt, so nautilus wasn't running,) and ctrl-alt-F2 to get into a console. Then:

**sudo umount /media/hdb1** to unmount the volume.

**sudo mv /media/hdb1 /media/share** to remane the mount point in /media.

**sudo nano /etc/fstab** to edit the entry for that volume, in the second column, changing it as /media/share like the step above. This is necessary to keep the change after a reboot.

**sudo mount -a** to remount the volumes listed in /etc/fstab, and apply your change.

Then I ctrl-alt-F7 and logged back into ubuntu, and it had the change as well. One side-effect it had that was puzzing, was that the 'Computer' icon on the nautilus toolbar lost it's image, but still worked fine.

There may still be a way to do this all through nautilus, possible running it as root, but I tired of trying to find it.

---

### Post by aaron321ca on 2005-09-29
Ah yes, that worked.  Such a simple solution too - next time I should consider simplicity first, as opposed to hunting for a complex workaround for 2 hours :-)

Thank you very much!

---

### Post by SilentCacophony on 2005-09-29
No problem. :) If you ever find yourself trying out window managers without gnome or kde running, working from the commandline like that is generally the way to do it, anyway.

---

