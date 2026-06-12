---
title: "Kernel Cleanup"
date: 2006-09-21
forum: Desktop Environments
---

### Post by seismicmike on 2006-09-21
Hey, I just upgraded from Breezy to Dapper and I just noticed on my GRUB that I now have 3 different Ubuntu Kernels listed. Is there any reason why I would need the old ones? Can I delete them? How do I go about doing this?

---

### Post by FyreBrand on 2006-09-21
I like to have the previous kernel version available in case the upgrade broke something.  The others I remove.  You can remove them using Synaptic: (menu) System -> Administration -> Synaptic Package Manager.

It's not too tricky but make sure you only remove the older versions and not the general image type or the restricted kernel modules.

When you open Synaptic look in the "Base System" modules section.  You want to remove the older kernel version.  So if I was going to remove my last kernel version I would choose to remove "linux-image-2.6.15-26-686".  There are two options when removing a package, either "Mark for Removal" or "Mark for Complete Removal".  I normally choose "Mark for Complete Removal" because, if I understand correctly, it will remove the package from from the drive as well as uninstalling it and that it also updates/remove config files associated with the package.  That's just what I do, but you might want to research that a bit closer.

I just want to say it again: I would recommend leaving the previous kernel version installed unless you are absolutely sure of yourself that you want to remove it.

---

### Post by ayoli on 2006-09-21
if you really don't need your old kernels you can remove them with synaptics, aptitude or apt-get.

---

### Post by james99 on 2006-09-21
excellant advice. Removed my oldest kernal and got back 80 MBs. Thank you

---

### Post by seismicmike on 2006-09-22
Sweet, it works great! Thanks

---

