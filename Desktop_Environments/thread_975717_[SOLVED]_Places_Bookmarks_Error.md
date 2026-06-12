---
title: "[SOLVED] Places Bookmarks Error"
date: 2008-11-08
forum: Desktop Environments
---

### Post by jajodo on 2008-11-08
Since upgrading to 8.10 from 8.4 my Places Bookmarks links are broken.

Sometimes Places-Home folder causes totem to load
Always Places-Home folder or Places-Bookmarks do not open Nautilus.

Interestingly the same links work normally if nautilus is opened using Places-Computer

I initially did an internet upgrade and the problem was there.
Later I just did a clean install (for several reasons) with Home being on a separate partition and the problem persists.

I would guess these links must be stored somewhere in the Home directory and a file there must be corrupt.

My thanks for any ideas.

---

### Post by frendofthedevil on 2008-11-08
I have the same problem, except my Places --> x folders always seems to open individual movies I have on the hard drive.  I'll be watching for a fix...

---

### Post by jajodo on 2008-11-09
Success.  Apparently this is a known bug.  This worked for me.


-right click any directory in your home directory after opening places->computer
-choose Properties->Open With->File Browser and close.

If the file browser option is not there you can "add" nautilus

Good luck

---

