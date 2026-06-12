---
title: "TiEmu"
date: 2009-03-10
forum: General Help
---

### Post by Stoodle on 2009-03-10
I want to run a TI-89 emulator on my computer but I can't get TiEmu to compile. Any suggestions? this is what I'm getting:

```

tiemu-3.02/src/gdb/gdb/c-lang.c:472: undefined reference to `c_parse'
gdb/gdb/libgdb.a(c-lang.o):(.rodata+0x284): undefined reference to `c_error'
gdb/gdb/libgdb.a(c-lang.o):(.rodata+0x364): undefined reference to `c_error'
gdb/gdb/libgdb.a(c-lang.o):(.rodata+0x3e4): undefined reference to `c_error'
gdb/gdb/libgdb.a(c-lang.o):(.rodata+0x464): undefined reference to `c_error'
collect2: ld returned 1 exit status
make[2]: *** [tiemu] Error 1
make[2]: Leaving directory `/home/tetrix/tiemu-3.02/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/tetrix/tiemu-3.02'
make: *** [all] Error 2

```

---

### Post by exXplode on 2009-09-18
what about using the ubuntu package found in multiverse?

install like this:
```
sudo aptitude install tiemu-skinedit tiemu
```

then just run tiemu

original TI-89 Titanium Operating System rom download for use with tiemu: [TI-89 Titanium Operating System v3.10]("http://education.ti.com/downloads/files/89/TI89Titanium_OS.89u")

greetings

---

