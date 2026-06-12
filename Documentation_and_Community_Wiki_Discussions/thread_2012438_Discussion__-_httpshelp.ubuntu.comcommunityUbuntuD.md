---
title: "Discussion  - https://help.ubuntu.com/community/UbuntuDesktopLVM"
date: 2012-06-29
forum: Documentation and Community Wiki Discussions
---

### Post by nothingspecial on 2012-06-29
Please use this thread for discussion regarding

[http://ubuntuforums.org/showthread.php?t=1782296](http://ubuntuforums.org/showthread.php?t=1782296)

Support threads should be posted in normal forums.

Thank you.

---

### Post by KisteBecks on 2012-09-29
IMPORTANT:  a install with this method did fail in the end, the kernel couldnt boot. /dev/mapper/vgpool wasnt available.
ther ALTERNATE install cd does come with lvm support and is needed!


i really like the article but you might want to add this:

if you already have a lvm setup before you need to run:
vgscan
vgchange -a y sysvg

to make the old entries available to the kernel like pointed out by pcas.

---

### Post by chuckyp on 2013-03-08
Fixed section on the post install instructions had echo foo &gt;&gt; /etc/modules to echo foo >> /etc/modules

---

### Post by vandor on 2013-06-11
I ran into an error on the very last command of the guide:

> Install LVM2 onto your chroot file system:
```
root@ubuntu:/# apt-get -y install lvm2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package lvm2 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'lvm2' has no installation candidate
```

I found that I had to update the lists of packages with apt-get before that last command would work:
```
root@ubuntu:/# apt-get update
```

---

### Post by kf6kjg on 2013-10-28
I know it's an optional section, but it's worth noting that _before_ incanting
```

sudo chroot /mnt

```
 the following stanzas would be VERY helpful:
```

cp -L /etc/resolv.conf /mnt/etc/
mount -t proc none /mnt/proc
mount --rbind /sys /mnt/sys
mount --rbind /dev /mnt/dev

```
(Adapted from the [Gentoo Handbook]("http://www.gentoo.org/doc/en/handbook/handbook-x86.xml?full=1#book_part1_chap6__chap1") - I used to use Gentoo, was a very good learning experience, but I no longer have the time to maintain it... :()

The first stanza makes it so your chroot can access the network, the rest make sure everything else is functional so that no operations will choke.

---

