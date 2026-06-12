---
title: "Can't Get Liero AI to run on Linux"
date: 2005-07-17
forum: Gaming &amp; Leisure
---

### Post by jamsea on 2005-07-17
I tried downloading and playing Liero AI ([http://helios.et.put.poznan.pl/~sskowron/liero/index.html](http://helios.et.put.poznan.pl/~sskowron/liero/index.html)) on Ubuntu but all I get is this error when I try to play it:

Runtime error 216 at 0x08080301
  0x08080301
  0x0807FFE0
  0x0805179E
  0x0805288F
  0x08052C21
  0x0807E5D3
  0x080840FE
  0x08048C3F
  0x08048C2C
  0x00000000

The weird thing is, it ran flawlessly on my old Debian system I had a while back. I downloaded all the SDL libraries with apt-get, so that shouldn't be the problem. Anyone else having the same problem, or am I just doing something really stupid? Thanks in advance!

---

### Post by elephanthunter on 2005-07-29
I know this topic is old, but I'm having the exact same problem with Liero-AI. I too used it on debian and got it to work just fine -.-

Has anybody found a way to get it running?  :)

(The source code was written in Pascal, but I don't know if that would create a runtime error like this)

---

### Post by Unaligned on 2008-11-17
I'm sorry to resurrect this old thread, but in case anyone wants it, I've rebuilt Liero-AI on Ubuntu 8.04. It should now run with more recent systems. Again, really sorry about the long delay, but then again it's been 6 years since I last touched that code.

Anyway it's on the [usual download site]("http://helios.et.put.poznan.pl/~sskowron/liero/download.html") as version 2.02. I made two tiny bugfixes, and apart from that it's pretty much equivalent to 2.01. Same broken English in places too :-#

---

### Post by Dedoimedo on 2008-11-17
Hello,

A few solutions that you might like:

1. Run the old, original liero in dosbox (emulated).
2. Try another flavor of liero (there are many).
3. Try a windows version of liero through wine.

Dedoimedo

---

