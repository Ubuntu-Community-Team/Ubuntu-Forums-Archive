---
title: "Symbolic links on LXDE desktop (Red circles with white exclamation mark)"
date: 2014-08-20
forum: Desktop Environments
---

### Post by tomsam2 on 2014-08-20
Hi,

Lubuntu 14.04 64 bit, with current updates

I installed Lubuntu (fresh install) on one of my older systems, and now encounter the following behaviour:

When I create symbolic links (ln -s or via PCManFM) to directories on the Desktop, they are shown correctly and double click opens them.

But  sometimes when I log on later, the links are shown as red circles with white exclamation marks, and on double click, I'm asked to specify the application to use (as if it was an unknown file type).

If I then change the name of the link or move it (mv) from the desktop and back, it works as expected again.

So, what am I doing wrong?

Two of the links are on the same file system, one of the links is on an unmounted file system, if that matters.

lrwxrwxrwx 1 tomsam tomsam 27 Aug 19 16:45 dia -> /home/tomsam/Documents/ddia
lrwxrwxrwx 1 tomsam tomsam 58 Aug 19 16:45 german -> /home/tomsam/Documents/forpublish/german
lrwxrwxrwx 1 tomsam tomsam 36 Aug 19 16:45 darktable2 -> /media/tomsam/CommonData/darktable2

Regards,
tomsam


PS I would have added a file here that shows the part of my desktop, but it seems local files are not allowed here.

---

