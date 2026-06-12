---
title: "Compiling gpsbabel 1.3.6 on Intrepid"
date: 2009-01-06
forum: General Help
---

### Post by d-lang on 2009-01-06
I am trying to get gpsbabel 1.3.6.  I see that version 1.3.5 is in the repo, but the newer version appears to have better support for what I'm trying to accomplish.

I can not figure out why the package will not build.  I don't have much experience doing this, so any help would be appreciated.

I issue the following command:

```
david@Trilian:~/Desktop/gpsbabel-1.3.6$ . ./configure --host=i686-pc-linux-gnu && make

```

The configure script runs; make displays a number of warnings and ends with:

```
gtrnctr.c:467: error: 'gtc_rd_deinit' undeclared here (not in a function)
make: *** [gtrnctr.o] Error 1
$ exit

```

If I run configure without the "--host=i686-pc-linux-gnu" option I get:

```
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... bash: error: cannot run C compiled programs.
If you meant to cross compile, use `--host'.

```

Attached is the full output from the "./configure --host=i686-pc-linux-gnu && make" command.  Again, any help is appreciated.

---

