---
title: "I can't install Open Raider"
date: 2009-08-11
forum: Gaming &amp; Leisure
---

### Post by commodore256 on 2009-08-11
The debian package installer says:
```
Error: Dependency is not satisfiable: xlibs (>> 4.1.0)
```

I tried sudo apt-get install xlibs
```
Package xlibs is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
```

I tried sudo apt-get -f install xlibs

```
Package xlibs is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
```

I tried looking for it with google and launchpad doesn't always help.

x86 binary doesn't work either.

```
I tried compiling it by running make

make[1]: *** [bin/debug/math.o] Error 1
make[1]: Leaving directory `/home/cj/Desktop/OpenRaider-0.1.0'
make: *** [debug] Error 2

```

Does anybody know how to fix this?

---

### Post by DirtDawg on 2009-08-12
The latest activity recorded on the [Open Raider SourceForge page]("http://sourceforge.net/projects/openraider/") is from 2003. Xlibs has most likely been phased out of the Debian/Ubuntu repositories and replaced by something else. Unfortunately, with the latest release being six years old, Open Raider doesn't seem to have kept up.

Unless you really want to spend a lot of time working on this, I recommend moving on.

---

