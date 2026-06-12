---
title: "df -h - no avail space, strange problem"
date: 2010-04-18
forum: Desktop Environments
---

### Post by mag_dex on 2010-04-18
Hey,

I have a following problem. If I type df -h I get 
```

magnus@debian:~/Downloads$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda1             9.7G  9.2G     0 100% /
tmpfs                 760M     0  760M   0% /lib/init/rw
udev                   10M  332K  9.7M   4% /dev
tmpfs                 760M   12K  760M   1% /dev/shm
/dev/hda2             9.1G  6.6G  2.1G  77% /home
/dev/hda4             128G  126G     0 100% /home/magnus/stuff
/dev/mapper/truecrypt1
                      6.4G  6.1G  321M  96% /media/truecrypt1

```
I can't save any new files because there is no avail. space. 
However, as you can see not all space is Used.
If I remove any file avail. space will not change :|

I don't know what to do. Removing files doesn't help me. There is still 0 avail.

---

### Post by micio on 2010-04-19
keep in mind that 5% of disk space is reserved to root.

You can reclaim this space by

```
# tune2fs -m xxx /dev/sdXY
```

where xxx is the percent number that you would reserve (also 0 is accepted)

however it is not suggested for root filesystem.

---

