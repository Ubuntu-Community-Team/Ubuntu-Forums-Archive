---
title: "knetworkconf fixed"
date: 2005-06-03
forum: Desktop Environments
---

### Post by randyman on 2005-06-03
Hello friends. I've read a lot of threads in this forum about the problem with knetworkconf when setting the default gateway in a static IP configuration, resulting always in a blank value. I have great news for all of you. According to the makers of ASLinux Desktop, a Spanish Debian-based distro, it seems to be a bug that affects that kind of distros, like Kubuntu, MEPIS or the own ASLinux Desktop, They've patched the source, recompiled it and built a new .deb package.

As a ASLinux Desktop user, I don't know if this package will work with Kubuntu, but I think it possibly will as they use KDE 3.3 and Kubuntu uses 3.4.

URLS:

Forum thread: [http://www.activasistemas.com/exec/modulo=nforos/sc=mensajes/id_foro=24/id_padre=183](http://www.activasistemas.com/exec/modulo=nforos/sc=mensajes/id_foro=24/id_padre=183)
Package: [http://apt.aslinux.com/aslinux2/main/binary-i386/updates/knetworkconf_0.6.1-2.aslinux-1_i386.deb](http://apt.aslinux.com/aslinux2/main/binary-i386/updates/knetworkconf_0.6.1-2.aslinux-1_i386.deb)

I hope this helps all of you with this problem.

---

### Post by philipacamaniac on 2005-06-03
Extract the diff from the deb source package, and post it as an attachment to this bug:
[https://bugzilla.ubuntu.com/show_bug.cgi?id=9871](https://bugzilla.ubuntu.com/show_bug.cgi?id=9871)

Or, if you don't have an Ubuntu Bugzilla account, just post the diff here, and I will add it to the bug.

---

