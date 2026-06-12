---
title: "libgl1-mesa* packages missing for reinstall?"
date: 2006-09-27
forum: Desktop Environments
---

### Post by enigma_0Z on 2006-09-27
I am trying to reinstall the mesa packages so that the libgl symlinks are proper again for my ATI card. I am changing over to the opensource drivers since ATI is no longer supporting my supposedly ancient card (it's a Radeon 9000). Anyways, I am trying to reinstall libgl1-mesa-dri in particular, but apt says that it can't reinstall the pacakage because it cannot be downloaded again. Has anyone else had this problem as well? This was an upgrade from a long time again from a breezy install, would/should/could that matter? I think that I might have something missing in my list.

(/etc/apt/sources.list for reference):
```

deb http://archive.ubuntu.com/ubuntu dapper-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu dapper-updates main restricted

deb http://archive.ubuntu.com/ubuntu dapper main universe multiverse restricted
deb-src http://archive.ubuntu.com/ubuntu dapper main universe multiverse restricted

deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted

deb http://security.ubuntu.com/ubuntu dapper-security universe
deb-src http://security.ubuntu.com/ubuntu dapper-security universe

## Penguin Liberation Front
deb http://packages.freecontrib.org/ubuntu/plf/ breezy free non-free
deb-src http://packages.freecontrib.org/ubuntu/plf/ breezy free non-free

## Freenx
deb http://free.linux.hp.com/~brett/seveas/freenx breezy-seveas freenx

## XGL
#deb http://xgl.compiz.info dapper main

## BMPX
deb http://files.beep-media-player.org/packages/ubuntu dapper main universe

```

---

