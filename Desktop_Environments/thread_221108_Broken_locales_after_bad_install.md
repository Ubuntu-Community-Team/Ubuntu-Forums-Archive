---
title: "Broken locales after bad install"
date: 2006-07-22
forum: Desktop Environments
---

### Post by JeffreyRatcliffe on 2006-07-22
I just tried installing to Dapper the version of hplip from Edgy, hoping to sort out some printer issues I am having. Unfortunately, there were a load of dependencies and one of them broke my locales. So I'd like it back as it was. 

The Synaptic log in question is:

```
Removed the following packages:
hplip-ppds

Upgraded the following packages:
foomatic-filters-ppds (20060406-0ubuntu1) to 20060530-2
gcc-4.1-base (4.1.1-2) to 4.1.1-9ubuntu1
hpijs (2.1.7+0.9.7-4ubuntu1) to 2.1.10+0.9.11-2ubuntu4
hplip (0.9.7-4ubuntu1) to 0.9.11-2ubuntu4
hplip-data (0.9.7-4ubuntu1) to 0.9.11-2ubuntu4
libc6 (2.3.6-15) to 2.4-1ubuntu6
libc6-dev (2.3.6-15) to 2.4-1ubuntu6
libc6-i686 (2.3.6-15) to 2.4-1ubuntu6
libffi4 (4.1.1-2) to 4.1.1-9ubuntu1
libffi4-dev (4.1.1-2) to 4.1.1-9ubuntu1
libgcc1 (1:4.0.3-1ubuntu5) to 1:4.1.1-9ubuntu1
libsnmp-base (5.2.1.2-4ubuntu2) to 5.2.2-4ubuntu1
libsnmp9 (5.2.1.2-4ubuntu2) to 5.2.2-4ubuntu1
libssl0.9.8 (0.9.8a-7build1) to 0.9.8b-2
libstdc++6 (4.0.3-1ubuntu5) to 4.1.1-9ubuntu1
libusb-0.1-4 (2:0.1.10a-22ubuntu1) to 2:0.1.12-2
sysv-rc (2.86.ds1-6ubuntu32) to 2.86.ds1-14.1ubuntu2
xbase-clients (7.0.0-0ubuntu45) to 1:1.1
xfonts-100dpi (6.8.2.1-5) to 1:1.0.0-2
xfonts-75dpi (6.8.2.1-5) to 1:1.0.0-2
xfonts-base (6.8.2.1-5) to 1:1.0.0-3
xfonts-scalable (6.8.2.1-5) to 1:1.0.0-4
xutils (7.0.0-0ubuntu45) to 1:1.1

Installed the following packages:
hpijs-ppds (2.1.10+0.9.11-2ubuntu4)
python-central (0.5.1)
xkb-data (0.8-7ubuntu1)
```

I've played with things like ```
apt-get install package=version
``` and aptitude to no avail. Anybody got any good ideas?

Thanks

Jeff

---

