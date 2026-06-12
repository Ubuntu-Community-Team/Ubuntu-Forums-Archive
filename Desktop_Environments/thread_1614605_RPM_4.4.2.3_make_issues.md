---
title: "RPM 4.4.2.3 make issues"
date: 2010-11-05
forum: Desktop Environments
---

### Post by suryaemlinux on 2010-11-05
Hi,
I'm using Ubuntu 10.04 and trying to compile RPM 4.4.2.3 source. I received the following error and I dunno what to do with that. My gcc version is 4.4.3 and make version is 3.81

[B]/usr/lib/libbeecrypt.so: undefined reference to `GOMP_parallel_sections_start'
/usr/lib/libbeecrypt.so: undefined reference to `GOMP_parallel_end'
/usr/lib/libbeecrypt.so: undefined reference to `GOMP_sections_next'
/usr/lib/libbeecrypt.so: undefined reference to `GOMP_sections_end_nowait'
collect2: ld returned 1 exit status
make[3]: *** [rpmdb_archive] Error 1
make[3]: Leaving directory `/root/Downloads/rpm-4.4.2.3/rpmdb'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/root/Downloads/rpm-4.4.2.3/rpmdb'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/root/Downloads/rpm-4.4.2.3'
make: *** [all] Error 2
[/B]

Thanks for your help.

---

