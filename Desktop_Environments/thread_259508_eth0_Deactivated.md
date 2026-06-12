---
title: "eth0 Deactivated"
date: 2006-09-17
forum: Desktop Environments
---

### Post by macogw on 2006-09-17
When I got on my computer today, there was one update.  It was a kernel image.  I installed it, and it needed a restart, so I did that.  Now my computer doesn't recognize a wired ethernet connection.  Hunting through the log, I found that eth0 was deactivated.  I tried ifconfig eth0 up, but it says:
eth0: ERROR while getting interface: No such device
and just ifconfig eth0 returns:
eth0: error fetching interface information: Device not found

How do I make it see my ethernet card again?

---

### Post by lamego on 2006-09-17
Just read the green warning on the top of the main page here on the forum.

---

### Post by macogw on 2006-09-17
That has nothing to do with my problem.  I do not have a nvidia card, the display is fine, that blue screen thing is not happening.  This is my ethernet card, and this was todays update, not that old one that screwed everyone else up.

I see the part at the end, but is there a way I can just remove that update?  Without internet, when a fix is released, I will not be able to get it anyway.

---

### Post by lamego on 2006-09-17
You should be able to boot with the previous kernel which is listed on your boot menu, anyway the previous version should be on /var/cache/apt/archives.
Check with:
```
ls /var/cache/apt/archives/*linux*
```
You can install it with:
```
sudo dpkg -i package_name
```

---

### Post by macogw on 2006-09-17
/var/cache/apt/archives/linux-image-2.6.15-26-386_2.6.15-26.47_i386.deb
/var/cache/apt/archives/linux-kernel-devel_2.6.15-26.47_all.deb
/var/cache/apt/archives/linux-restricted-modules-2.6.15-26-386_2.6.15.11-4_i386.deb
/var/cache/apt/archives/linux-restricted-modules-common-2.6.15.11-4_all.deb
/var/cache/apt/archives/linux-source-2.6.15_2.6.15-26.47_all.deb

which one?

---

