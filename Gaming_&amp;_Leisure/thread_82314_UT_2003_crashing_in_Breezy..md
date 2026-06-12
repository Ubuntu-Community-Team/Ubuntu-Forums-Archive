---
title: "UT 2003 crashing in Breezy."
date: 2005-10-26
forum: Gaming &amp; Leisure
---

### Post by z-vet on 2005-10-26
Hi all. 
UT 2003 crashing with segfault or with:

```
zvet@3g0:~$ /mnt/hd/games/ut2003/ut2003

Developer Backtrace:
[ 1]  ./ut2003-bin [0x84b5e70]
[ 2]  [0xffffe420]
[ 3]  ./ut2003-bin(_ZN11FQuadStream13GetSpriteDataEv+0x1316) [0x8404cd6]
[ 4]  ./ut2003-bin(_ZN11FQuadStream13GetStreamDataEPv+0x58) [0x8402c88]
[ 5]  ./ut2003-bin(_ZN25FOpenGLVertexStreamARB_VA11AddVerticesEP13FVertexStream+0xb8) [0x8602db8]
[ 6]  ./ut2003-bin(_ZN22FOpenGLRenderInterface16SetDynamicStreamE13EVertexShaderP13FVertexStream+0xe6) [0x85fa536]
[ 7]  ./ut2003-bin(_ZN14SpriteIterator4DrawEP9AxEmitterP10FSceneNode+0x17c) [0x83f8c3c]
[ 8]  ./ut2003-bin(_ZN9AxEmitter6RenderEP15FLevelSceneNodeP16FRenderInterface+0x4e7) [0x83c5237]
[ 9]  ./ut2003-bin(_ZN13FDynamicActor6RenderEP15FLevelSceneNodeP5TListIP13FDynamicLightEPS2_IP20FProjectorRenderInfoEP16FRenderInterface+0x1cce) [0x827d97e]
[10]  ./ut2003-bin [0x82a10fb]
[11]  ./ut2003-bin(_Z11RenderLevelP15FLevelSceneNodeP16FRenderInterface+0x1334) [0x829e254]
[12]  ./ut2003-bin(_ZN15FLevelSceneNode6RenderEP16FRenderInterface+0x665) [0x82855f5]
[13]  ./ut2003-bin(_ZN16FPlayerSceneNode6RenderEP16FRenderInterface+0x1c5) [0x8289ee5]
[14]  ./ut2003-bin(_ZN11UGameEngine4DrawEP9UViewportiPhPi+0x13a9) [0x81cdb09]
[15]  ./ut2003-bin(_ZN12USDLViewport7RepaintEi+0x56) [0x85ebfa6]
[16]  ./ut2003-bin(_ZN10USDLClient4TickEv+0x159) [0x85ea879]
[17]  ./ut2003-bin(_ZN11UGameEngine4TickEf+0x422) [0x81d06d2]
[18]  ./ut2003-bin(_ZN9CMainLoop7RunLoopEv+0x3b1) [0x8128f71]
[19]  ./ut2003-bin [0x812113f]
[20]  ./ut2003-bin(main+0x294a) [0x811d73a]
[21]  /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xd2) [0xb7cddea2]
[22]  ./ut2003-bin(getlogin+0xad) [0x811abc1]
Signal: SIGILL [illegal instruction]
Aborting.

```

Can anyone tell me what this backtrace means, please?

---

### Post by daller on 2005-11-14
There has been some flaws in the linux-version of UT

Try to find the newest patch!

I'm using patch 3355 in UT2004 (Find the newest patch for UT2003)

my UT2004 never crashes since the update...

---

### Post by z-vet on 2005-11-15
Well, a newest patch is installed already. I think i need to check my RAM. Thanks anyway.

---

