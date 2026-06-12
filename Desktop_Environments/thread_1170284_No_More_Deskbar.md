---
title: "No More Deskbar?"
date: 2009-05-26
forum: Desktop Environments
---

### Post by Levviathor on 2009-05-26
I can't seem to find the deskbar.  It was there in Intrepid, but doesn't appear to be available in Jaunty.

Add to Panel doesn't have it, nor does Add/Remove Applications.

I looked for a download, but all I could find was a .tar.gz.  I tried to compile it, but got stuck at make.

Here's the error I got, following [_these instructions_]("www.tuxfiles.org/linuxhelp/softinstall.html"):
```
alex@alex-laptop:~/Dls/deskbar-applet-2.26.2$ make
make: *** No targets specified and no makefile found.  Stop.
```

I miss it :C


Note: I just thought to search Synaptic (genius, I know), and found three packages.  I'd download them, but I'm not sure how dependencies and whatnot would work out.
```
libdeskbar-tracker
deskbar-applet
deskbar-applet-dbg
```

---

### Post by jolx on 2009-05-26
just install 'deskbar-applet' from synaptic and it will handle any dependencies, or go to [apt://deskbar-applet]("apt://deskbar-applet")

---

### Post by Levviathor on 2009-05-26
Wow.

That was incredibly simple.

Thanks very much :D

---

