---
title: "Problems after uninstalling tango (for gdc)"
date: 2009-05-28
forum: General Help
---

### Post by kumoshk on 2009-05-28
I just installed tango for D through a shell script called tango-0.98-forDSSS-gdc-i686-pc-linux-gnu-withDSSS-withGDC.sh, but it messed up my regular D compiler installed through the Synaptic Package Manager (gdc). So, I uninstalled tango through an uninstall script that the said shell script installed, and it still doesn't work.

Anyway, here is the error I get when trying to compile with gdc:
/usr/local/bin/../lib/gcc/i686-pc-linux-gnu/4.1.2/../../../libgphobos.a(configunix.o): In function `htonl':
(.text+0x55): undefined reference to `_D3std9intrinsic5bswapFkZk'
collect2: ld returned 1 exit status

Any idea how to fix this without doing a reinstall of Ubuntu? I tried reinstalling gdc through the Synaptic Package Manager, but that doesn't do anything (I tried reinstalling several things that way). I've noticed that completely removing software through the said manager does not 'completely remove' everything about the software. Perhaps this is the reason reinstalling and/or removing the software and installing again doesn't do anything helpful.

---

