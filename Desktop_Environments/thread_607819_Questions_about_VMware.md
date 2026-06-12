---
title: "Questions about VMware"
date: 2007-11-09
forum: Desktop Environments
---

### Post by Mottq on 2007-11-09
I only have one question really:
I am currently running a dual boot system Ubuntu and Windows XP. Instead of a partitioned HD I have two HD's. My question is this-could I run my windows programs from the Wndows hard drive in VMware or must I re-install the wondoze app within the Virtual Machine?

---

### Post by carlosjuero on 2007-11-09
You have to reinstall the Windows applications in the VMWare machine.

---

### Post by spupy on 2007-11-09
You CAN run the Windows that is installed on your hardrive, but I don't recomment. I did it and screwed my windows install. (which wasn't that bad, now im 100% linux XD )

---

### Post by KOld Iron on 2007-11-09
To be more specific about this:

VMWare offers you the possibility to use an existing system on a physical disk drive to run as a Virtual Machine (instead of a separately installed system on a virtual disk drive, which would be the normal case). But even VMWare gives ample warning on doing that.

The problem is, that it creates the possibility that the physical disk drive is accessed from two places at the same time. I.e. access through your guest system (e.g. Windows) and your host system (e.g. Ubuntu). This could easily lead to data inconsistencies on that drive, thus rendering your guest system (i.e. Windows) inoperable. Even worse, if your guest system is running on the boot partition, it even may screw up your boot section in such a way, that you cannot boot either system afterwards.

So, it can be done (as said before), but you better back up (seriously!) your data before trying, because you may end up with installing two new systems in the worst case, if something goes wrong.

---

### Post by spupy on 2007-11-09
Another possible problem arises with the activation of windows. If you run windows from your current install in a VM, it will sense the different hardware and ask you to activate this copy. So after several boots between normal and vmware you got no more activation attempts and a dead windows copy. (That only applies if your windows copy is legal...)

---

### Post by mtbsoft on 2007-11-13
One way to avoid having to reinstall everything would be to clone the windows hard drive, using something like Ghost, then restore the image into the VM disk image - this way you would preserve all the settings from the original installs.  You will still have issues with windows activation detecting the apparent hardware change though.

---

