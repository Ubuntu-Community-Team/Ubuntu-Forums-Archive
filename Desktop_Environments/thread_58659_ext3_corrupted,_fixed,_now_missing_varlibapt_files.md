---
title: "ext3 corrupted, fixed, now missing /var/lib/apt files - help!"
date: 2005-08-21
forum: Desktop Environments
---

### Post by taygan on 2005-08-21
We lost power and the file system corrupted.

the boot up check found inconsistencies, and forced a manual fsck.

I said yes to fixing everything, I had to run it 3 times to clear the errors.

The root partition is messed up, though boots, /home is fine.


I ran a diagnostic the drive itself.  No problems with the drive.


Tried running synaptic, didn't work, tried apt-get didn't work.  Computer then locked up, and root was read only (ran e2fsck again)

Things are getting better, but my apt directory is empty.


```
sudo apt-get update
E: Could not open lock file /var/lib/apt/lists/lock - open (2 No such file or directory)
E: Unable to lock the list directory

```

Is there a way to recover the package information and rebuild the apt directory??



EDIT:  /var/lib/dpkg/info seems to have everything still.  Hopefully this means I still have my package lists/states??

---

### Post by taygan on 2005-08-22
Well, I took the plunge and started messing around with things.  I recreated the directories that were missing (according to the error messages) and apt-get started working again (thank goodness!)  I'll see if errors start going away..  

Something weird has happend with the ext3 journal.. It's looking like a ext2 stuff..  I'll pursue it further.

---

