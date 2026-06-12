---
title: "TWINKLE 0.5 build problems"
date: 2006-01-03
forum: General Help
---

### Post by coaxx on 2006-01-03
Hi all,

Sip Softphone  Twinkle 0.5 Version is out. There is no deb package out there and i tried to compile it.

I got the following error during configuring:

```

uwe@ubuntu:~/Desktop/desktop-files/twinkle/twinkle-0.5$ export QTDIR=/usr/share/qt3
uwe@ubuntu:~/Desktop/desktop-files/twinkle/twinkle-0.5$ ./configure
checking build system type... i686-pc-linux
checking host system type... i686-pc-linux
.
.
.
.
checking for int... yes
checking size of int... configure: error: cannot compute sizeof (int), 77
See `config.log' for more details.

```

Does anybody know what **checking size of int... configure: error: cannot compute sizeof (int), 77** means? Google did not help :(

here is config.log

```

.
.
blabla
.
.
#ifdef __cplusplus
extern "C" void std::exit (int) throw (); using std::exit;

configure: exit 1
..

```

I tried to convert a suse rpm to deb, but twinkle allways crashes with htis package.

---

