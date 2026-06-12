---
title: "doom3-demo - reverts to software rendering?!"
date: 2009-09-14
forum: Gaming &amp; Leisure
---

### Post by bartman on 2009-09-14
Hi!

I got a bit nostalgic today and remembered there was a native D3 port. I installed the demo just to see if everything works and to my surprise it crashed. I had compiz enabled and direct rendering was set to no. I disabled effect, logged out and in and after that the demo kind of started.

Unfortunately the picture took forever to draw and I could do little else than to switch to a vty and kill the program. Fortunately a log was left for me in the gnome-terminal i launched the demo from. From scanning over it quickly it seems the graphics pipeline deterirates to software rendering.

Can anyone help me get this demo to run properly? My hardware is a ATi Radeon Mobility X700 (RV410 / M26) and it should run this game fine. Since Ubuntu 9.04 i can only use the open source driver, xserver-xorg-video-radeon.

Full log is attached. Here's the snip of the log file I think is most telling:
> $ doom3-demo
...
*********************************WARN_ONCE*********************************
File r300_render.c function r300Fallback line 383
Software fallback:ctx->Stencil.Ref[0] != ctx->Stencil.Ref[back] || ctx->Stencil.ValueMask[0] != ctx->Stencil.ValueMask[back] || ctx->Stencil.WriteMask[0] != ctx->Stencil.WriteMask[back]
***************************************************************************
...
Terminated


Thanks for your help.

---

