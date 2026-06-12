---
title: "cifs share mount appears both as device and as network location in nautilus"
date: 2018-09-09
forum: Desktop Environments
---

### Post by eXecu7or on 2018-09-09
Hello,

I'm mounting a share location at boot via an entry in fstab that looks like this:

```
//192.168.1.50/BIG /media/BIG cifs comment=systemd.automount,username=anonymous,password=,rw,dir_mode=0777,file_mode=0777 0 0
```

When navigation to "Other locations" in Nautilus, I get it both as a device (1) and as a network location (2) , as in the picture below.
[ATTACH=CONFIG]281036[/ATTACH]

I'm interested in keeping just one of them in Nautilus, either / or. Would be interested in knowing how to achieve that for both of them.

Additionaly, I have a partition that I'm also mounting via FSTAB:

```
UUID=d828924c-0d1d-4cd5-b9b7-1820f843dfa7 /media/STORAGE ext4 comment=systemd.automount,nosuid,nodev,nofail,noauto 0 0
```

It appears as a a device (3) in nautilius, I would however like it hidden as it is mounted in a specific folder.

Thank you.

---

### Post by TheFu on 2018-09-10
Always keep the real mounts (fstab or autofs or with a manual "mount"), which will perform faster than the GVFS mounts (point-n-click), normally used by nautilus.
I have no idea how to convince any file namager to forget gvfs mounts.  Perhaps removing those packages?

---

### Post by eXecu7or on 2018-09-10
Played around with gnome-disks, at least I got some other windows partitions to not appear.

What packages should I try removing?

---

