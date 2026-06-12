---
title: "usb start up disc"
date: 2009-04-25
forum: General Help
---

### Post by tanveerahmed2k8 on 2009-04-25
i made a start up disc with ubuntu 8.10 on my memory stick and now that thiers a newer ubuntu, how would i put the new 1 on? i dont want to format my memory stick it has 7 gb of data that i backed up from windows.

---

### Post by aikiwolfie on 2009-04-25
Personally I'd use a separate memory stick or partition for the backed-up data or burn it to a DVD. If you want multiple Live USB images on one disc you'll need to get to grips with the boot loader used with Live distributions. Which is different from GRUB. It's called SysLinux or some such.

I've been considering something similar myself. I have an 8GB USB drive. I want to set it up so it has the 32-bit and 64-bit Live versions on separate partitions and then a separate partition for temporary backed up data or useful shell scripts etc. A bootable MS-DOS partition might also be useful.

---

### Post by tanveerahmed2k8 on 2009-04-25
> **aikiwolfie said:**
> Personally I'd use a separate memory stick or partition for the backed-up data or burn it to a DVD. If you want multiple Live USB images on one disc you'll need to get to grips with the boot loader used with Live distributions. Which is different from GRUB. It's called SysLinux or some such.

I've been considering something similar myself. I have an 8GB USB drive. I want to set it up so it has the 32-bit and 64-bit Live versions on separate partitions and then a separate partition for temporary backed up data or useful shell scripts etc. A bootable MS-DOS partition might also be useful.

so.. how do i over write it??

---

### Post by Monotoko on 2009-04-25
The USB disk startup creator will let you choose to im sure

just backup the other 7GB of data, then use the USB startup disk creator

---

### Post by aikiwolfie on 2009-04-25
If the USB startup creator doesn't let you overwrite the existing version on the USB disk, just go to the USB drive and delete the files using Nautilus. Then go back to the USB start-up disk utility and it should let you continue.

Just remember to move those backed-up Windows files first. That's your first job.

---

### Post by tanveerahmed2k8 on 2009-04-26
this is gona take for ever moving all those backed up files...

---

### Post by aikiwolfie on 2009-04-26
So you've learned a valuable lesson. Always keep your data seperate from your OS.

---

