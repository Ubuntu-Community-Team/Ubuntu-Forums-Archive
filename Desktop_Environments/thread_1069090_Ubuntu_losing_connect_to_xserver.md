---
title: "Ubuntu losing connect to xserver"
date: 2009-02-13
forum: Desktop Environments
---

### Post by nsalyzyn on 2009-02-13
Hi,

I use my Ubuntu machine (8.04) mainly for programming and use a windows emacs as my text editor, opened from the terminal.  At random intervals, my machine has begun losing it's connection to the xserver.  The error message that appears when I open up emacs it says something like:

No protocol specified
emacs: unable to open display ":0.0"

I type 'xhost' and it has the same error message.

The odd thing, is that I can "ssh -Y" to this machine and still open up emacs terminals just fine.  After some time (I think when my screensaver kicks in) the xserver locks up entirely.

Also, when this error occurs, all of the icons to open up software no longer works.

---

### Post by nsalyzyn on 2009-02-17
Is this an known problem with 64 bit machines?

---

### Post by nsalyzyn on 2009-02-20
For any curious, I figured this out.  I had opened too many 'ssh -Y' connections and had consistently been doing so... Ooops.

---

