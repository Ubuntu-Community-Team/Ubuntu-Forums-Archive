---
title: "Can mount but cant fstab"
date: 2009-04-02
forum: General Help
---

### Post by rbriggin on 2009-04-02
Im trying to mount a hfsplus drive with fstab but am having trouble getting it to work correctly

I can mount it manually with 

```
mount -t hfsplus /dev/sdb1 /media/mac
```

but my fstab line
```
/dev/sdb1 /media/mac hfsplus users,auto,rw,gid=1001,dmask=000,fmask=000 0 0
```

wont mount the drive

i tried adding 
```
hfsplus
```
to my /etc/modules file but that didnt help

Any ideas?

---

### Post by caver1 on 2009-04-02
Once you have mounted your drive look in mtab.
Find the mount for it in mtab and then copy it over to fstab.
caver1

---

### Post by rbriggin on 2009-04-02
Awesome thanks

---

