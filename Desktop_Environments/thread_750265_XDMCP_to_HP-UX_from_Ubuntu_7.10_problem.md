---
title: "XDMCP to HP-UX from Ubuntu 7.10 problem"
date: 2008-04-09
forum: Desktop Environments
---

### Post by Elrie on 2008-04-09
Hi to all!


Server side - HP-UX 11i v3
Client - Gutsy 7.10

Plain ssh login works fine.

I  tried different XDMCP variants already.

1. Using remote login from GDM login screen
    I can see remote server, but attempt to connect push me back to GDM screen.

2. tsclient (Xnest)
   I connect and see CDE login screen (XDM)
   I could type login name
   I type password but...
   When I type any number or special simbol in password I'll get error:
 
  FreeFontPath: FPE "/usr/share/fonts/X11/misc" refcount is 2, should be 1; fixing.

  And clients try to reconnect.

3. clean Xnest from CLI. I try to locate fonts manually.
    The problem the same as in 2. Font paths don't matter at all.

Any ideas?

---

### Post by Elrie on 2008-04-10
More info....

Trying Xephyr gives more error info.
Result - the same


Error message:

```
Extended Input Devices not yet supported. Impelement it at line 625 in ../../../../hw/kdrive/src/kinput.c
FreeFontPath: FPE "/usr/share/fonts/X11/misc" refcount is 2, should be 1; fixing.
```

------------

P.S.

Doesn't matter - first line not the error...

So situation the same as before

---

### Post by Elrie on 2008-04-10
It seems problem not on Ubuntu side...

Tried the same clients from CentOS 5.1

Same errors.
So it may be HP-UX problem.

---

