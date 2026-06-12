---
title: "External HDD trouble"
date: 2009-02-22
forum: General Help
---

### Post by 89c51 on 2009-02-22
Hello

this morning i woke up and when i tried to browse my external HDD i came up with this picture 

[[img]http://xs536.xs.to/xs536/09080/error807.png.xs.jpg[/img]](http://xs.to/xs.php?h=xs536&d=09080&f=error807.png)

instead of the weird ASCI filenames i expected to find 3 folders

after the initial shock i went into dmesg and found that its full of

```
[84372.149860] sdc1: rw=0, want=11156967798, limit=488392002
[84372.150055] attempt to access beyond end of device
[84372.150059] sdc1: rw=0, want=11156967774, limit=488392002
[84372.150468] attempt to access beyond end of device
[84372.150473] sdc1: rw=0, want=5373022569, limit=488392002
[84372.150677] attempt to access beyond end of device
[84372.150680] sdc1: rw=0, want=5373022558, limit=488392002

```

i run sudo fsck.vfat /dev/sdc1 -av but it hanged 

i run ubuntu hardy and the hdd is formated in FAT32

any help would be welcome

---

