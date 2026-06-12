---
title: "how do i uninstall ubuntu"
date: 2009-06-19
forum: General Help
---

### Post by suffery on 2009-06-19
i need to uninstall ubuntu and gnome booter..
i used the disk and it wont completely uninstall gnome is still there and so is ubuntu..

if i just factory reset windows xp will it get rid of it?
i dont have a windows disk

---

### Post by Bigtime_Scrub on 2009-06-19
If you reinstall windows that will get rid of Ubuntu. If you have a factory reset like a dedicated "safe" partition that lets you reload windows then that will erase Ubuntu too.

---

### Post by suffery on 2009-06-19
so i just do the normal factory reset in windows.
i dont have to change any settings or anything?
also will windows get its portion space back?

---

### Post by Bigtime_Scrub on 2009-06-19
> **suffery said:**
> so i just do the normal factory reset in windows.
i dont have to change any settings or anything?
also will windows get its portion space back?

I have to admit I am unsure what a normal factory reset does? Do you mean restore point or is there some sort of partitioning done?

---

### Post by Bigtime_Scrub on 2009-06-19
Most PC's sold within the last couple of years have a recovery utility built in that allows you to revert the system back to manufacturer settings - that means wiping the drive(s) and reinstalling the default software that was included with the system.

If this is what you are trying to do, check your Start menu. For Dell (what I use), it's called the Dell Recovery Center. Other manufacturers will call it something similiar. You may also have the option at boot-up to start a recovery utility.

---

### Post by suffery on 2009-06-19
i know how to do it. i have emachines.
but will it work
i want it to get rid of ubuntu gnome booter and all.

---

### Post by camper365 on 2009-06-19
> **suffery said:**
> i know how to do it. i have emachines.
but will it work
i want it to get rid of ubuntu gnome booter and all.
If you want to get rid of Ubuntu, you can just use GParted (from the livecd) and delete the Ubuntu partitions and resize the Windows partition (defragment first).
Getting rid of GRUB will be trickier. If you can start the Windows recovery console (from a Windows CD or maybe from the recovery partition on your hard drive) then you can use the command fixmbr and that will fix it perfectly.

---

