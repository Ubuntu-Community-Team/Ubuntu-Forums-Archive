---
title: "Problem with RPG"
date: 2009-05-29
forum: General Help
---

### Post by madmaxou on 2009-05-29
Hi,
I'm having problems with an internet rpg called regnum online. It always terminates with a segmentation fault (Got SIGSEGV...). In a previous thread someone told me to upgrade my xserver-xorg-core and my xorg-drivers but that doesn't help. (Also these things about Memory allocation don't work if someone knows this problem already)

Thanks in advance

I'm using an ATI Radeon 9600, 2 GB Ram and Karmic.

---

### Post by madmaxou on 2009-05-29
This is what i get:
```
max@max-desktop:~$ cd regnum; ./rolauncher
max@max-desktop:~/regnum$ Saving backtrace to crash_backtrace_5997.log
Got SIGSEGV (segmentation fault)
```

---

### Post by iO.Parabola on 2009-05-29
can you paste the log?

---

### Post by madmaxou on 2009-05-29
> **iO.Parabola said:**
> can you paste the log?

This is the backtrace:

libs/libcore_client.so(_ZN10ClientBase14save_backtraceEv+0x79) [0xb7c2b9]
libs/libcore_client.so(_ZN10ClientBase12client_crashEi+0x1b) [0xb7c58b]
[0xc73400]
/usr/lib/libGL.so.1 [0x16aced6]
libs/libopengl_api.so(_ZN8Engine3D12RenderizerGL20init_graphics_systemEiiibb+0xc26) [0x7a25c6]
libs/libcommon_entities.so(_ZN13DisplayEntity15creation_notifyEP7Message+0x4bc) [0x87d7ac]
libs/libentity_system.so(_ZN13EntityManager32initialize_entity_as_custom_typeEPKciS1_P7MessageP6Entity+0x483) [0xbf5b23]
libs/libregnum_client.so(_ZN10GameClient19initialize_entitiesEv+0x2af) [0x28363f]
libs/libregnum_client.so(_ZN10GameClient4initEiPPc+0x876) [0x2867b6]
libs/libregnum_client.so(_ZN10GameClientC1EiPPc+0xf3) [0x287703]
./game(main+0x259) [0x8048fc9]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5) [0x1955775]
./game(__gxx_personality_v0+0x61) [0x8048c71]

---

### Post by madmaxou on 2009-05-29
anyone an idea???

---

