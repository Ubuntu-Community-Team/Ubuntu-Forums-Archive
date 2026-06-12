---
title: "Compositing segfaults X"
date: 2010-11-08
forum: Desktop Environments
---

### Post by dr_duck on 2010-11-08
Hi,

I have kde4 installed on my ubunto 10.10

When I use kde4, if compositing is enabled (opengl) X segfaults and dumps me to a terminal (not gdm).  If I restart gdm & try kde again it logs in, but in Boring Mode (no effects).  

Looking in .kde4/kderc (or wherever) I find that kde has marked OpenGLIsUnsafe=true.  setting it to false & logging in again crashes X as before.

Compositing works fine in gnome - either using metacity's own compsiting or using compiz (which is what I use).

Something that kwin is doing is causing X to segfault.

I'm using ubuntu 10.10 64 bit using the opensouce radeon driver on an ati xpress 200M.

---

