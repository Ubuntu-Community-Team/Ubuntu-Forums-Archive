---
title: "unable to compile"
date: 2006-08-01
forum: Desktop Environments
---

### Post by ubun_nv on 2006-08-01
i was ubable to compile a new kernel 2.6.16.20.

i got this error

Using /usr/src/linux-headers-2.6.15-23 as source for kernel
  /usr/src/linux-headers-2.6.15-23 is not clean, please run 'make mrproper'
  in the '/usr/src/linux-headers-2.6.15-23' directory.
make[1]: *** [prepare3] Error 1
make: *** [_all] Error 2


after running make mrproper in /usr/src/linux-headers-2.6.15-23.

i got this error

scripts/Makefile.clean:17: /usr/src/linux-headers-2.6.15-23/drivers/infiniband/ulp/srp/Makefile: No such file or directory
make[3]: *** No rule to make target `/usr/src/linux-headers-2.6.15-23/drivers/infiniband/ulp/srp/Makefile'.  Stop.
make[2]: *** [drivers/infiniband/ulp/srp] Error 2
make[1]: *** [drivers/infiniband] Error 2
make: *** [_clean_drivers] Error 2


please help

---

