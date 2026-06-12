---
title: "configuration problem with external USB HDD"
date: 2005-12-24
forum: General Help
---

### Post by joft on 2005-12-24
Hi,

I have a configuration problem with an external USB HDD. I have already google'd for HOWTOs and general documentation for HAL, but didn't find really useful stuff.

So here is my question:

The external HDD has two partition (first vfat and second ext3). As soon as I plug in the external HDD two new icons appear on my gnome desktop - this is ok. But: The partitions are not mounted to the same mount point each time. Sometimes partition one is /media/usbdisk and partition two is /media/usbdisk-1 and sometimes its the other way round.

I would like to configure my system in a way, that

1) the vfat partition gets mounted with my own custom gid, fmask, dmask, umask, iocharset ... options

2) both partitions are mounted to the same mount point *everytime* I plug them in

3) both partitions get mounted with the options sync and dirsync (I think this would be good for external media).

My system is Ubuntu 5.10, Kernel 2.6.12. And I think that HAL, pmount and gnome-volume-manager are somehow responsible for the automounting feature. So I guess somehow I have to configure them the right way ....

Can anybody tell me, if this is possible? Are there any HowTos? General documentation for HAL? (I think HAL is the one program which is the basis for the whole thing and gnome-volume-manager is just using it).

---

### Post by joft on 2005-12-27
Hi,

meanwhile I found a solution ... I just oversaw the "HAL spec" link on HALs homepage - sorry.

Everything you need is detailed there. But I found out that pmount-hal (used by gnome-volume-manager) takes the default locale of your system and puts it into the iocharset mount options. But the kernel complains about using UTF-8 for VFAT ... does anybody know why?

Anyway, I just modified pmount/pmount-hal to recognize the HAL device object property "volume.policy.mount_options.iocharset". This way, I can force him to use e.g. iso8859-1 as iocharset.
And I had to add recognition of the "utf8" mount option of VFAT (volume.policy.mount_options.utf8). Don't ask me why, but only with this the german "Umlaute" appear right ...

That's it. Ask me if you need any details :D ...

---

### Post by gostal on 2006-09-07
> **joft said:**
> Hi,

 But the kernel complains about using UTF-8 for VFAT ... does anybody know why?


Half a year ago I had serious problems mounting USB storage FAT32 volumes using utf8. Some files and directories created using WinXP simply didn't show up. Also I could not write to the FAT volumes. iso8859-1 was necessary to get this right. For the german umlaut possibly you'd have to go for iso8859-15 instead. But that was half a year ago. Things could have happened to both utf8 and the vfat driver since then and warning messages is perhaps not the first priority so it could be that this is not an issue anymore. Hard coding utf8 into pmount isn't something on would do without good reason.  

Gösta

---

