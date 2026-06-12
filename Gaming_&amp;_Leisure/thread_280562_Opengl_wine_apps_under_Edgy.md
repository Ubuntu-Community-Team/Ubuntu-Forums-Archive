---
title: "Opengl wine apps under Edgy"
date: 2006-10-19
forum: Gaming &amp; Leisure
---

### Post by deadlydeathcone on 2006-10-19
Has anyone had any luck running OpenGl apps under wine in Edgy Eft using the default Via drivers? About 90% of the apps I've tried bomb out with the following message:

```
main/renderbuffer.c:2041: _mesa_add_renderbuffer: Assertion `bufferName == BUFFER_DEPTH || bufferName == BUFFER_STENCIL || fb->Attachment[bufferName].Renderbuffer == ((void *)0)' failed.
```

Does anyone know of a work around, or is this bug report material? Here's the backtrace, for reference:

```
Backtrace:
=>1 0xffffe410 (0xffffe410)
  2 0xb7cecef3 abort+0x103 in libc.so.6 (0xb7cecef3)
  3 0xb7ce4dbb __assert_fail+0xfb in libc.so.6 (0xb7ce4dbb)
  4 0x7e53d5e1 _mesa_add_renderbuffer+0x161 in unichrome_dri.so (0x7e53d5e1)
  5 0x7e4d0e1d in unichrome_dri.so (+0x22e1d) (0x7e4d0e1d)
  6 0x7e4d1449 viaMakeCurrent+0x79 in unichrome_dri.so (0x7e4d1449)
  7 0x7e4cd6b0 in unichrome_dri.so (+0x1f6b0) (0x7e4cd6b0)
  8 0x7e6ddb6c in libgl.so.1 (+0x17b6c) (0x7e6ddb6c)
  9 0x7e6dfd2f glXMakeContextCurrent+0x27f in libgl.so.1 (0x7e6dfd2f)
  10 0x7e6dffc3 glXMakeCurrent+0x23 in libgl.so.1 (0x7e6dffc3)
  11 0x7bf58cf9 in wined3d (+0x38cf9) (0x7bf58cf9)
  12 0x7bf5b56b IWineD3DImpl_FillGLCaps+0x22cb in wined3d (0x7bf5b56b)
  13 0x7bf5d834 in wined3d (+0x3d834) (0x7bf5d834)
  14 0x7ea27a10 in ddraw (+0x27a10) (0x7ea27a10)
  15 0x7ea28422 DirectDrawCreateEx+0xf9 in ddraw (0x7ea28422)
  16 0x00405293 in wf (+0x5293) (0x00405293)
  17 0x7ea26772 DirectDrawEnumerateExA+0xa2 in ddraw (0x7ea26772)
  18 0x00405a42 in wf (+0x5a42) (0x00405a42)
  19 0x0045d1b8 in wf (+0x5d1b8) (0x0045d1b8)
  20 0x61666544 (0x61666544)
  21 0x02c3f608 (0x02c3f608)
  22 0x00000000 (0x00000000)
```

If anyone wants to test, [Warning Forever]("http://www18.big.or.jp/~hikoza/Prod/index_e.html") is a good, 716 kb example.

---

### Post by apanloco on 2006-11-30
I also have this problem. Have you figured it out, or has anyone else a solution?

I am using the via driver.

/D

---

### Post by hikaricore on 2006-11-30
> **deadlydeathcone said:**
> Has anyone had any luck running OpenGl apps under wine in Edgy Eft using the default Via drivers? About 90% of the apps I've tried bomb out with the following message:

```
main/renderbuffer.c:2041: _mesa_add_renderbuffer: Assertion `bufferName == BUFFER_DEPTH || bufferName == BUFFER_STENCIL || fb->Attachment[bufferName].Renderbuffer == ((void *)0)' failed.
```

Does anyone know of a work around, or is this bug report material? Here's the backtrace, for reference:

```
Backtrace:
=>1 0xffffe410 (0xffffe410)
  2 0xb7cecef3 abort+0x103 in libc.so.6 (0xb7cecef3)
  3 0xb7ce4dbb __assert_fail+0xfb in libc.so.6 (0xb7ce4dbb)
  4 0x7e53d5e1 _mesa_add_renderbuffer+0x161 in unichrome_dri.so (0x7e53d5e1)
  5 0x7e4d0e1d in unichrome_dri.so (+0x22e1d) (0x7e4d0e1d)
  6 0x7e4d1449 viaMakeCurrent+0x79 in unichrome_dri.so (0x7e4d1449)
  7 0x7e4cd6b0 in unichrome_dri.so (+0x1f6b0) (0x7e4cd6b0)
  8 0x7e6ddb6c in libgl.so.1 (+0x17b6c) (0x7e6ddb6c)
  9 0x7e6dfd2f glXMakeContextCurrent+0x27f in libgl.so.1 (0x7e6dfd2f)
  10 0x7e6dffc3 glXMakeCurrent+0x23 in libgl.so.1 (0x7e6dffc3)
  11 0x7bf58cf9 in wined3d (+0x38cf9) (0x7bf58cf9)
  12 0x7bf5b56b IWineD3DImpl_FillGLCaps+0x22cb in wined3d (0x7bf5b56b)
  13 0x7bf5d834 in wined3d (+0x3d834) (0x7bf5d834)
  14 0x7ea27a10 in ddraw (+0x27a10) (0x7ea27a10)
  15 0x7ea28422 DirectDrawCreateEx+0xf9 in ddraw (0x7ea28422)
  16 0x00405293 in wf (+0x5293) (0x00405293)
  17 0x7ea26772 DirectDrawEnumerateExA+0xa2 in ddraw (0x7ea26772)
  18 0x00405a42 in wf (+0x5a42) (0x00405a42)
  19 0x0045d1b8 in wf (+0x5d1b8) (0x0045d1b8)
  20 0x61666544 (0x61666544)
  21 0x02c3f608 (0x02c3f608)
  22 0x00000000 (0x00000000)
```

If anyone wants to test, [Warning Forever]("http://www18.big.or.jp/~hikoza/Prod/index_e.html") is a good, 716 kb example.

Hmm... alot of that backtrace is Direct3D related, are you sure you're running the software in OpenGL mode?  And you're also it looks like trying to run them with Wine..  Have you tried any native linux games?  Also make sure direct rendering is enabled for your video card:

```
glxinfo | grep rendering
```

should return a: **Yes**

---

### Post by ninevoltz on 2007-01-13
I have the same problem, only I am using Fedora Core 6. It has to be the openchrome via driver, because Wine works fine with the same games on my Fedora machine that has an ATI card and another that has an NVIDIA card. It doesn't look like anyone has worked on the openchrome drivers for ages. There is no support for GLX/AIGLX either, so no desktop effects too. I wish I had the knowledge to fix it myself! All of the 3D Linux games work fine, just not Wine or Cedega. I don't get it.

---

### Post by Raznog on 2007-02-06
i have the same problem and when  i did 

glxinfo | grep rendering

it tells me

Xlib:  extension "XFree86-DRI" missing on display ":1.0".
direct rendering: No

---

