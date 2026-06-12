---
title: "vlc"
date: 2005-11-28
forum: Deferred/Invalid Requests
---

### Post by zenrox on 2005-11-28
[http://lists.ubuntu.com/archives/dapper-changes/2005-November/001851.html](http://lists.ubuntu.com/archives/dapper-changes/2005-November/001851.html)
back port please ??;)

---

### Post by strikeforce on 2005-11-29
> 
E: Build-Depends dependency for vlc cannot be satisfied because the package libdvbpsi4-dev cannot be found
I couldn't resolve build dependencies by myself. I'll drop you to a shell
[email]marc@ubuntu:~/ubp-compile-temp/vlc-0.8.4.debi[/email]an$ apt-cache search libdvbpsi
libdvbpsi3 - library for MPEG TS and DVB PSI tables decoding and generating
libdvbpsi3-dev - development files for libdvbpsi3



I'm not sure whether jdong wants to backport libdvbpsi4 and dev

---

### Post by jdong on 2005-11-29
Does not build -- libflac-dev (>= 1.1.2-3)  cannot be satisfied under Breezy.

---

### Post by zenrox on 2005-11-30
[QUOTE=jdong]Does not build -- libflac-dev (>= 1.1.2-3)  cannot be satisfied under Breezy.[/QUOTE]
NUTS

---

