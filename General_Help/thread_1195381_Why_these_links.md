---
title: "Why these links?"
date: 2009-06-23
forum: General Help
---

### Post by Krupski on 2009-06-23
Hi all,

Look at this listing of my server root directory:

```

root@storage:/# ls -laF
total 88
drwxr-xr-x  21 root root  4096 2009-06-23 18:00 ./
drwxr-xr-x  21 root root  4096 2009-06-23 18:00 ../
drwxr-xr-x   2 root root  4096 2009-06-23 16:51 bin/
drwxr-xr-x   3 root root  4096 2009-06-23 18:01 boot/
drwxr-xr-x  15 root root  3880 2009-06-23 18:02 dev/
drwxr-xr-x  85 root root  4096 2009-06-23 18:02 etc/
drwxr-xr-x   3 root root  4096 2009-06-23 17:47 home/
[COLOR="Red"][B]lrwxrwxrwx   1 root root    32 2009-06-23 18:00 initrd.img -> boot/initrd.img-2.6.28-13-server
lrwxrwxrwx   1 root root    32 2009-06-23 16:45 initrd.img.old -> boot/initrd.img-2.6.28-11-server[/B][/COLOR]
drwxr-xr-x  13 root root  4096 2009-06-23 17:59 lib/
lrwxrwxrwx   1 root root     4 2009-06-23 16:39 lib64 -> /lib/
drwx------   2 root root 16384 2009-06-23 16:38 lost+found/
drwxr-xr-x   2 root root  4096 2009-06-23 17:01 media/
drwxr-xr-x   2 root root  4096 2009-04-13 05:33 mnt/
drwxr-xr-x   2 root root  4096 2009-06-23 16:39 opt/
dr-xr-xr-x 140 root root     0 2009-06-23 14:02 proc/
drwx------   2 root root  4096 2009-06-23 17:55 root/
drwxr-xr-x   2 root root  4096 2009-06-23 18:00 sbin/
drwxr-xr-x   2 root root  4096 2009-03-06 12:16 selinux/
drwxr-xr-x   2 root root  4096 2009-06-23 16:39 srv/
drwxr-xr-x  12 root root     0 2009-06-23 14:02 sys/
drwxrwxrwt   5 root root  4096 2009-06-23 18:02 tmp/
drwxr-xr-x  11 root root  4096 2009-06-23 16:49 usr/
drwxr-xr-x  14 root root  4096 2009-06-23 16:52 var/
[COLOR="Red"][B]lrwxrwxrwx   1 root root    29 2009-06-23 18:00 vmlinuz -> boot/vmlinuz-2.6.28-13-server
lrwxrwxrwx   1 root root    29 2009-06-23 16:45 vmlinuz.old -> boot/vmlinuz-2.6.28-11-server[/B][/COLOR]

```

Note the items in red. Why are these links here and what do they do, if anything?

Grub boots from the /boot directory anyway, and indeed removing the links in the root directory does not cause the system to fail to boot.

Are they just there for information... or are they leftovers from an earlier time (when they had to be in the root) or what?

Any info will be appreciated. Thanks!

-- Roger

---

### Post by Krupski on 2009-09-23
> **Krupski said:**
> Hi all,

Look at this listing of my server root directory:

```

root@storage:/# ls -laF
total 88
drwxr-xr-x  21 root root  4096 2009-06-23 18:00 ./
drwxr-xr-x  21 root root  4096 2009-06-23 18:00 ../
drwxr-xr-x   2 root root  4096 2009-06-23 16:51 bin/
drwxr-xr-x   3 root root  4096 2009-06-23 18:01 boot/
drwxr-xr-x  15 root root  3880 2009-06-23 18:02 dev/
drwxr-xr-x  85 root root  4096 2009-06-23 18:02 etc/
drwxr-xr-x   3 root root  4096 2009-06-23 17:47 home/
[COLOR="Red"][B]lrwxrwxrwx   1 root root    32 2009-06-23 18:00 initrd.img -> boot/initrd.img-2.6.28-13-server
lrwxrwxrwx   1 root root    32 2009-06-23 16:45 initrd.img.old -> boot/initrd.img-2.6.28-11-server[/B][/COLOR]
drwxr-xr-x  13 root root  4096 2009-06-23 17:59 lib/
lrwxrwxrwx   1 root root     4 2009-06-23 16:39 lib64 -> /lib/
drwx------   2 root root 16384 2009-06-23 16:38 lost+found/
drwxr-xr-x   2 root root  4096 2009-06-23 17:01 media/
drwxr-xr-x   2 root root  4096 2009-04-13 05:33 mnt/
drwxr-xr-x   2 root root  4096 2009-06-23 16:39 opt/
dr-xr-xr-x 140 root root     0 2009-06-23 14:02 proc/
drwx------   2 root root  4096 2009-06-23 17:55 root/
drwxr-xr-x   2 root root  4096 2009-06-23 18:00 sbin/
drwxr-xr-x   2 root root  4096 2009-03-06 12:16 selinux/
drwxr-xr-x   2 root root  4096 2009-06-23 16:39 srv/
drwxr-xr-x  12 root root     0 2009-06-23 14:02 sys/
drwxrwxrwt   5 root root  4096 2009-06-23 18:02 tmp/
drwxr-xr-x  11 root root  4096 2009-06-23 16:49 usr/
drwxr-xr-x  14 root root  4096 2009-06-23 16:52 var/
[COLOR="Red"][B]lrwxrwxrwx   1 root root    29 2009-06-23 18:00 vmlinuz -> boot/vmlinuz-2.6.28-13-server
lrwxrwxrwx   1 root root    29 2009-06-23 16:45 vmlinuz.old -> boot/vmlinuz-2.6.28-11-server[/B][/COLOR]

```

Note the items in red. Why are these links here and what do they do, if anything?

Grub boots from the /boot directory anyway, and indeed removing the links in the root directory does not cause the system to fail to boot.

Are they just there for information... or are they leftovers from an earlier time (when they had to be in the root) or what?

Any info will be appreciated. Thanks!

-- Roger

Bump...

---

