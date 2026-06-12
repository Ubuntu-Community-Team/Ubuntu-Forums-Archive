---
title: "/var/www/cache &gt; tmpfs"
date: 2009-04-20
forum: General Help
---

### Post by anjanesh on 2009-04-20
I want to add this line in my /etc/fstab
```
none /var/www/cache tmpfs nr_inodes=200k,mode=01777,nosuid,nodev 0 0,size=2GB
```
Is this okay ?

Thanks

---

### Post by sdennie on 2009-04-20
It's probably ok but, I'm not sure if you need some of that information.  On my machine (with 4G of RAM), the default size of tmpfs is already 2G.  Just using the defaults and an explicitly set "mode=" will probably do exactly what you are trying to do.

Edit:
I should also point out that if you are doing this for performance reasons, it may not have as much of an impact as you think it will.  That data is probably already cached in my memory if it's being used a lot.

---

