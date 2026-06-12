---
title: "Mupen64 Crashes"
date: 2007-04-18
forum: Gaming &amp; Leisure
---

### Post by noerrorsfound on 2007-04-18
Mupen 64 crashes with each video plugin I try to use. I recently used the same ROM (Perfect Dark) in Windows on Mupen64 and it worked (on all plugins if I remember correctly, although some were slower than others).

Nearly all of the plugins crash with this error:
> Signal number 11 caught:
        errno = 0 (Success)

The only plugin that doesn't crash with that error is 5 - TR64 OpenGL v0.7.8, which just freezes up Mupen64 and displays this in the console:
> Xlib: unexpected async reply (sequence 0xc379)!
I'm running Ubuntu 64 bit which I am thinking is the problem. I tried to compile the plugins but first they said I didn't have SDL libraries when I did, and when I found a fix for that on the forum then I was told I didn't have GTK+-2.0.

---

### Post by Sockerdrickan on 2007-04-18
Have you installed gtk2 dev

---

### Post by noerrorsfound on 2007-04-18
I found and installed the GTK dev package (I hadn't seen it before).

I tried to compile mupen64 again but it just said that "something went wrong" and since mupen64 works but the plugins don't, I was going to try to compile glide64.

It tells me this:
> compiletex.c:1: error: CPU you selected does not support x86-64 instruction set
make: *** [compiletex.o] Error 1

---

