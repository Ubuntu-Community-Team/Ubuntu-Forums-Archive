---
title: "lvm i/o error"
date: 2006-06-14
forum: Desktop Environments
---

### Post by slava on 2006-06-14
hello,
i am using lvm 2 with dapper and having problems with home partition. when i try activating my vg group "playbox" i get an error:
```
vgchange -ay
  /dev/evms/lvm2/playbox/home: read failed after 0 of 4096 at 0: Input/output error
  /dev/playbox/home: read failed after 0 of 4096 at 0: Input/output error
  7 logical volume(s) in volume group "playbox" now active
```
i tried 
```
e2fsck /dev/playbox/home
e2fsck 1.38 (30-Jun-2005)
e2fsck: Attempt to read block from filesystem resulted in short read while trying to open /dev/playbox/home
Could this be a zero-length partition?
```
can anyone please help me recover my partition :confused: 
thanks alot
slava

---

### Post by slava on 2006-06-23
can anyone please help me on this problem ? :)
all my important data is inaccessible right now ](*,) 

blessings
slava

---

### Post by slava on 2006-06-27
somebody please help ](*,)

---

