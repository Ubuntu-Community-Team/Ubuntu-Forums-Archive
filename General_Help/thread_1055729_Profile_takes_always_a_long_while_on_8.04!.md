---
title: "Profile takes always a long while on 8.04!"
date: 2009-01-31
forum: General Help
---

### Post by Fixman on 2009-01-31
I use Ubuntu 8.04 and recently have been experimenting with the Profile option, but the problem is that each time I boot it keeps a long while on "creating a new profile", instead of only the first time. Heres my menu.lst:

```

splashimage=(hd0,0)/boot/grub/splashimages/matrix.xpm.gz
default saved
timeout 5
color cyan/blue white/green

title Ubuntu
root (hd0,0)
kernel /boot/vmlinuz-2.6.24-23-generic root=UUID=a2c75bfd-dc90-4a34-92e8-4b52e2b9e3f6 ro quiet splash profile
initrd /boot/initrd.img-2.6.24-23-generic
quiet
savedefault 0

title Windows
root (hd1,0)
makeactive
chainloader +1
savedefault 0

```

---

### Post by Fixman on 2009-01-31
bump

---

