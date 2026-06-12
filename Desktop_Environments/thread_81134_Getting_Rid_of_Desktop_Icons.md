---
title: "Getting Rid of Desktop Icons"
date: 2005-10-23
forum: Desktop Environments
---

### Post by ScootsMcGee on 2005-10-23
I thought I had seen this somewhere in this forum before, but after extensive searching, I can't find it again.  So I'm making a new one.

I just started using Breezy, and went ahead and immediately mounted my other drives on the system.  All went well, but they added those annoying icons on the desktop automatically.  Since it was only two, and other people used the system, I figured I wouldn't worry about it.  But now I've created mounts for iso files and a couple other partitions (and accidentally mounted an iso to a taken mount, so that doubled an icon).

So now my desktop is cluttered with annoying icons that I can't delete.  I can't even unmount one of my iso directories because when I accidentally mounted two disks onto it, it apparently angered the mounting gods...

So in short, how can I ditch all of these icons, preferably without umounting.  I find it's quite sufficient to have the links in the Places drop down without needing the icons in the first place.

---

### Post by Kyral on 2005-10-23
[QUOTE=ScootsMcGee]I thought I had seen this somewhere in this forum before, but after extensive searching, I can't find it again.  So I'm making a new one.

I just started using Breezy, and went ahead and immediately mounted my other drives on the system.  All went well, but they added those annoying icons on the desktop automatically.  Since it was only two, and other people used the system, I figured I wouldn't worry about it.  But now I've created mounts for iso files and a couple other partitions (and accidentally mounted an iso to a taken mount, so that doubled an icon).

So now my desktop is cluttered with annoying icons that I can't delete.  I can't even unmount one of my iso directories because when I accidentally mounted two disks onto it, it apparently angered the mounting gods...

So in short, how can I ditch all of these icons, preferably without umounting.  I find it's quite sufficient to have the links in the Places drop down without needing the icons in the first place.[/QUOTE]
Quite easy. Fire up the GConf Editor (System Tools -> Configuration Editor) and navigate to /apps/nautilus/desktop and clear the checkbox for volumes_visible

---

### Post by migueljacq on 2005-10-23
I have my music folder mounted on a separate partition. In my fstab file I tell it to mount to /home/miguel/music
then I mount it again, and it goes into the above directory.
in contrast, not giving it such a direction means it mounts on the Desktop by default.

EDIT: above, even easier :-)

---

### Post by ScootsMcGee on 2005-10-23
Ok great, that got them off the desktop, thanks.

However, in the places menu (where I'd like the icons to stay so I can navigate to them quickly) there are still multiple icons for the same mount left.  For instance, I create a mount1 and mount 2 directory for iso mounting.  Without unmounting the disks I had in them, I accidentally mounted another 2 disks, and the result is the disks succesfully mounted in the respective directory, but created new icones (mount1 (2) and mount2 (2).  Can I get rid of those all together?

But thanks again for helping me get those things off the desktop.

---

### Post by ScootsMcGee on 2005-10-24
Is there anyone that can help with with the latter problem?

---

