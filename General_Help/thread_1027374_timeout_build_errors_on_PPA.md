---
title: "timeout build errors on PPA"
date: 2009-01-01
forum: General Help
---

### Post by nightfrost on 2009-01-01
I've just started learning packaging, and been trying out ppa a little.
I'm seeing this issue when trying to build ffado:

```
Session terminated, killing shell...make: *** wait: No child processes.  Stop.
make: *** Waiting for unfinished jobs....
make: *** wait: No child processes.  Stop.
semop(1): encountered an error: Identifier removed
 ...killed.
Build killed with signal 15 after 150 minutes of inactivity
******************************************************************************
Build finished at 20090101-0524
FAILED [dpkg-buildpackage died]
Purging chroot-autobuild/build/buildd/libffado-2.0~rc1
------------------------------------------------------------------------------

```

full log is here:
[http://launchpadlibrarian.net/20838950/buildlog_ubuntu-intrepid-amd64.libffado_2.0~rc1-0ubuntu1_FAILEDTOBUILD.txt.gz](http://launchpadlibrarian.net/20838950/buildlog_ubuntu-intrepid-amd64.libffado_2.0~rc1-0ubuntu1_FAILEDTOBUILD.txt.gz)

Does anyone know why this is? I've never seen any issue like this when compiling locally on my own computer.

Thanks.

---

### Post by nightfrost on 2009-01-01
I seem to have this problem with basically anything that depends on scons. Here's what I get when trying to build ardour 2.7:

```
Session terminated, killing shell...semop(1): encountered an error: Identifier removed
make: *** [debian/stamp-scons-build] Error 1
 ...killed.
Build killed with signal 15 after 150 minutes of inactivity
******************************************************************************
Build finished at 20090101-1825
FAILED [dpkg-buildpackage died]
Purging chroot-autobuild/build/buildd/ardour-2.7.1
------------------------------------------------------------------------------

```

Does anybody know anything about this? Should I file a bug report?

---

### Post by ibuclaw on 2009-01-01
[EDIT]
Maybe have a look here:
[http://qandr.org/quentin/writings/debscons](http://qandr.org/quentin/writings/debscons)
Could this be your answer?

Regards
Iain

---

### Post by nightfrost on 2009-01-01
Thanks for your input. 

I don't think it's possible to access any files on the build system through ppa. And I'm not seeing this problem when compiling locally on my own machine.

I might have come up with a workaround: I've built scons from jaunty in my ppa, hoping that the ardour build uses the local version of scons instead of the intrepid package. It's compiling now, so I'll know in a while.

---

