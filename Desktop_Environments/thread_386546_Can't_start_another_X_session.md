---
title: "Can't start another X session"
date: 2007-03-17
forum: Desktop Environments
---

### Post by unimatrix on 2007-03-17
Hello

I'm using Ubuntu 6.10 on amd64.
I've switched from GDM to KDM and now I can't open more than one X session.

This is the error message (/var/log/Xorg.0.log) I get when I try to open a second session:
> /cut/
AUDIT: Sat Mar 17 12:07:58 2007: 4290 X: client 25 rejected from local host
AUDIT: Sat Mar 17 12:07:58 2007: 4290 X: client 25 rejected from local host
AUDIT: Sat Mar 17 12:07:58 2007: 4290 X: client 25 rejected from local host
AUDIT: Sat Mar 17 12:07:58 2007: 4290 X: client 25 rejected from local host
AUDIT: Sat Mar 17 12:07:58 2007: 4290 X: client 25 rejected from local host
AUDIT: Sat Mar 17 12:07:59 2007: 4290 X: client 25 rejected from local host
AUDIT: Sat Mar 17 12:07:59 2007: 4290 X: client 25 rejected from local host
AUDIT: Sat Mar 17 12:07:59 2007: 4290 X: client 25 rejected from local host
/cut/

I think something is wrong with the display envionment variable, but being a noob I have no idea how to use it.. It is currently set to: DISPLAY=:0


Any ideas?
Please help, this is really annoying because not only I can't open a secondary session but none of the VNC services work either.

---

