---
title: "Testing ati drivers 8.28.8 (dependency problem)"
date: 2006-08-20
forum: Desktop Environments
---

### Post by hexion on 2006-08-20
Hello.

ATI released his 8.28.8 drivers (still without support of aiglx).

I installed it yesterday. Seems to be a litle faster (gained a few fps with glxgears), but after doing a aptitude update/upgrade, I found this issue:

> fglrx-kernel-2.6.15-26-386: Depende: xorg-driver-fglrx (= 8.27.10-1) pero está instalado 8.28.8-1.

Everything seems to be ok, but I tried to remove that "error" installing the 8.27.10 version of xorg-driver-fglrx, so I unpackaged the driver 8.27.10 and:
> sudo dpkg -i xorg-driver-fglrx_8.27.10-1_i386.deb


But, surprise, after doing that aptitude upgrade still complains, now with the oposite dependency problem:

> fglrx-kernel-2.6.15-26-k7: Depende: xorg-driver-fglrx (= 8.28.8-1) pero está instalado 8.27.10-1.


Buggy set of drivers??  Everyone has this problem, or is it just mine? :-k

---

### Post by zasf on 2006-08-22
I had the same problem

the = sign in
```
fglrx-kernel-2.6.15-26-386: Depende: xorg-driver-fglrx (**=** 8.27.10-1) pero está instalado 8.28.8-1.
```

should be >=.

I solved the problem by manually editing the deb control file inside the deb package

---

