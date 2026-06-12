---
title: "can not unmount removable media, nepomuk is using it"
date: 2013-03-19
forum: Desktop Environments
---

### Post by barna on 2013-03-19
Hi,
I want to detach an external usb disk, but the system said it can not do so:
```

Could not unmount the following device: /media/home-backup
One or more files on this device are open in an application

```
Checking it:
```

prompt> fuser -m /media/home-backup
/media/home-backup:   2984
prompt> ps uax | grep 2984
barna     2984  3.7  0.7 103164 21884 ?        SNl  09:01   0:18 /usr/bin/nepomukservicestub nepomukfilewatch
barna    27012  0.0  0.0   4648   832 pts/2    S+   09:09   0:00 grep 2984

```
Even though I told nepomuk not to index removable media, and I have even quit nepomuk.

I am using kubuntu 12.10
Thanks

---

