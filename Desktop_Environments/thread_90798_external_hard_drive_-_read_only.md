---
title: "external hard drive - read only"
date: 2005-11-15
forum: Desktop Environments
---

### Post by gw90se on 2005-11-15
Forgive me if there is a fix somewhere for this, but I didn't find it in a search. I have an external USB hard drive that I use for backing up my computer and the wife's Windows box. I have it formatted as fat32. I know I have written to it before, but now it shows up as read only. Any ideas how to correct this so I can write to it?

Thanks

---

### Post by aysiu on 2005-11-15
Follow the instructions here:
[http://www.ubuntuguide.org/#automountfat](http://www.ubuntuguide.org/#automountfat)

It assumes your drive is /dev/hda1, but it probably isn't. To find out what it is, plug in your drive, and type ```
sudo fdisk -l
``` My guess is it's probably something like /dev/sda1 or /dev/sde1

---

### Post by gw90se on 2005-11-16
Thanks, I'll give that a try. I had seen it, but wondered if there would be a difference with 5.04 & 5.10 as there seems to have been in other places.

---

### Post by aysiu on 2005-11-16
[QUOTE=gw90se]Thanks, I'll give that a try. I had seen it, but wondered if there would be a difference with 5.04 & 5.10 as there seems to have been in other places.[/QUOTE] No, the Ubuntu Guide is outdated for a lot of things, but it's still good for the mounting of Windows partitions.

---

### Post by gw90se on 2005-11-16
Thanks, that seems to have done the trick. Like i said earlier, I was just concerned about what would work from 5.04 and what wouldn't.

---

