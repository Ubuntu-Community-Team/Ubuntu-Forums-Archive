---
title: "Can't run Unigine Heaven"
date: 2011-03-17
forum: Gaming &amp; Leisure
---

### Post by Dr.Paneas on 2011-03-17
Ok I have download the latest edition of the benchmark and I have all the latest drivers installed for my Intel Sandy bridge 2500K processor.

at first the problem was an OpenAl error. I fixed that by installing libopenl1 (or something like that).

Up to this point I get a blank screen...
```

**OpenGL error: invalid enum**
Object::loadWorld(): different surface names "mill_wings" "mill_wings_1"
Loading "heaven.world" 36218ms
Unigine~# render_hdr 2 && render_restart
[B]GLFrameBuffer::enable(): incomplete attachment
GLFrameBuffer::enable(): incomplete attachment
Heaven_x86: program/ir_to_mesa.cpp:2281: prog_src_register mesa_src_reg_from_ir_src_reg(ir_to_mesa_src_reg): Assertion `reg.index < (1 << 11)' failed.[/B]

```Any ideas ?

I don't know if that helps but I check that I have problem with libva
```

paneas@ubuntubox:~/Downloads/Unigine_Heaven-2.5$ vainfo 
libva: libva version 0.31.1
libva: va_getDriverName() returns 0
libva: Trying to open /usr/lib/dri/i965_drv_video.so
libva error: /usr/lib/dri/i965_drv_video.so init failed
libva: va_openDriver() returns -1
vaInitialize failed with error code -1 (unknown libva error),exit

```

---

### Post by Dr.Paneas on 2011-03-18
> **Dr.Paneas said:**
> Ok I have download the latest edition of the benchmark and I have all the latest drivers installed for my Intel Sandy bridge 2500K processor.

at first the problem was an OpenAl error. I fixed that by installing libopenl1 (or something like that).

Up to this point I get a blank screen...
```

**OpenGL error: invalid enum**
Object::loadWorld(): different surface names "mill_wings" "mill_wings_1"
Loading "heaven.world" 36218ms
Unigine~# render_hdr 2 && render_restart
[B]GLFrameBuffer::enable(): incomplete attachment
GLFrameBuffer::enable(): incomplete attachment
Heaven_x86: program/ir_to_mesa.cpp:2281: prog_src_register mesa_src_reg_from_ir_src_reg(ir_to_mesa_src_reg): Assertion `reg.index < (1 << 11)' failed.[/B]

```Any ideas ?

I don't know if that helps but I check that I have problem with libva
```

paneas@ubuntubox:~/Downloads/Unigine_Heaven-2.5$ vainfo 
libva: libva version 0.31.1
libva: va_getDriverName() returns 0
libva: Trying to open /usr/lib/dri/i965_drv_video.so
libva error: /usr/lib/dri/i965_drv_video.so init failed
libva: va_openDriver() returns -1
vaInitialize failed with error code -1 (unknown libva error),exit

```

I have fixed the libva error. I can run World of Padman and other games/benchmarks but not all of them. For example I am still unable to run Unigine... it says OpenGL error.

btw you can find the whole Guide [here]("http://wp.me/p1qJXE-a") at my blog. I use to keep notes just in case, so this might be useful again in a few days later.

---

