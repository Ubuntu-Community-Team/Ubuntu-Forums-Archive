---
title: "mounted hard icons on desk top"
date: 2007-01-30
forum: Desktop Environments
---

### Post by klein de usa on 2007-01-30
hi 
i have a dell xps i have multi booted, dos 6.22,  xp, and 6.10 edgy everything is great and went realy smoth but no mater what i do every time i boot into edgy i have two icons, dos 6.22 and hda3 on my desktop how can i stop them from being mounted when edgy is booted ? in grub i # the entreys out so they don't show up in grub screen at boot up but they are still on my desk top i do not wish for edgy to have excess to dos or xp or viseaversa . any one have any ideas ?

---

### Post by bustanil on 2007-01-30
Try to delete the lines that defines the mount points from** /etc/fstab** file. Note you must be logged in as root.

---

### Post by marklid on 2007-01-30
Alternatively you can comment out those lines in /etc/fstab instead of deleting them (by putting a # at the beginnng of the line), that way if you decide to use those discs at a later date you can uncomment them.

---

### Post by klein de usa on 2007-01-30
thank you very much 
i found the file in browser but it wont let me save it after i make the changes? from the desk top, how do i sing into root with my password?
also in terminal ho do i invoke it singing me on as root with my password?
sorry i'm new

---

### Post by taurus on 2007-01-30
Applications -> Accessories -> Terminal
```
gksudo gedit /etc/fstab
```

---

### Post by klein de usa on 2007-01-30
thank you Taurus
editing the file worked like a charm

---

### Post by klein de usa on 2007-01-30
thank you
 Bustanil and Marklid icons gone and edgy still works :D

---

### Post by marklid on 2007-01-30
No probs mate glad you got it sorted.

---

