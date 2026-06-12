---
title: "nmrDraw in Ubuntu Hardy"
date: 2008-09-17
forum: Education &amp; Science
---

### Post by nkjvcjs on 2008-09-17
I recently upgraded from Feisty to Hardy.  nmrDraw from nmrPipe worked fine in Feisty.  Now i get:

nmrdraw: ../../src/xcb_io.c:285: _XAllocID: Assertion `!(dpy->flags & (1L << 3))' failed.
Abort


I really need this to work.

Thanks,

Nicole

---

### Post by ilyasyildirim on 2008-10-13
Did you solve this problem? I also upgraded from Ubuntu 7.10 to 8.04 and I cannot use NmrDraw anymore. I am getting the same error message:

nmrdraw: ../../src/xcb_io.c:285: _XAllocID: Assertion `!(dpy->flags & (1L << 3))' failed.
Aborted

I need to solve this issue because I use it almost all the time. Thanks.

---

### Post by nkjvcjs on 2008-10-13
Yes.  If you go to NIH and Install their latest (and last) version, it works.  You have to change all of the font scales in the nmrDraw startup script to "small" to get it not to look funny, but it works.

---

### Post by evanspap on 2008-10-20
I don't understand why it works but I had the same problem. However I managed to start nmrDraw by calling xterm
 from ubuntu terminal. 
laptop:/D/NMRpipe>xterm
and then
laptop:/D/NMRpipe$: nmrDraw


I suppose xterm uses a slightly different x11 or it can just handle easier back versions compatibility.

If anyone understands where is the problem please post an explanation?!

---

### Post by MightyU on 2009-08-25
> Re: nmrDraw in Ubuntu Hardy
I don't understand why it works but I had the same problem. However I managed to start nmrDraw by calling xterm
from ubuntu terminal.
laptop:/D/NMRpipe>xterm
and then
laptop:/D/NMRpipe$: nmrDraw


I suppose xterm uses a slightly different x11 or it can just handle easier back versions compatibility.

If anyone understands where is the problem please post an explanation?! 
In Ubuntu 9.04, your solution does not work anymore (sort of same error: ../../src/xcb_io.c:378: _XAllocID: Assertion `ret != inval_id' failed.). Did you for a chance install some additional X libraries?
Thanks

---

