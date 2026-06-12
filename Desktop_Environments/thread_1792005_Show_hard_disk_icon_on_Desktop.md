---
title: "Show hard disk icon on Desktop"
date: 2011-06-27
forum: Desktop Environments
---

### Post by Neville Hillyer on 2011-06-27
I would be grateful if somebody could tell me how to put an icon for the main disk (not Computer) on my Ubuntu 10.04 desktop.

---

### Post by Morbius1 on 2011-06-27
I don't think you can create a Launcher for an entire disk but you can create one for the main Linux partition:

Right Click the Desktop
Select Create Launcher
Give it a name and for the command use this:
```
nautilus /
```

---

### Post by ajgreeny on 2011-06-27
I'm not quite sure what you want, but you can only put icons on the desktop for partitions as far as I'm aware, just as Morbius1 said.

Tell us more about what you want and what you want to do with it, and there may be a better answer.

---

### Post by Neville Hillyer on 2011-06-27
Sorry I did not reply sooner - I have been trying a few things.

I should have said volume and not disk. I tried to use a symlink of 'File System' but the links created were always broken - I am not sure why - any thoughts?

The launcher method works well and has the advantage that this item on the desktop can also be seen in the Desktop folder.

I had previously used gconf-editor but it is very limited and appears to put items on the Desktop without them being in the Desktop folder - not sure why - any thoughts on this?

I would prefer to create my own symlinks but, as I said earlier, they don't always work and I cannot find a way to remove the link emblem from the icon - can this be done?

---

### Post by Neville Hillyer on 2011-06-28
For the time being I have added a launcher to the top panel for the boot partition and home directory.

I have also set Nautilus preferences to auto-mount media. I hope this will include all media and not just removable media.

Is there any way to auto-mount to a panel rather than the Desktop?

How can I set mounted hard disks to only rotate when required?

---

