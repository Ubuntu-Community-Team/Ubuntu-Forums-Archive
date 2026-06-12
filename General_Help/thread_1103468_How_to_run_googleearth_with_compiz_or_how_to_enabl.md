---
title: "How to run googleearth with compiz or how to enable direct rendering"
date: 2009-03-22
forum: General Help
---

### Post by lunatico on 2009-03-22
Hello,

I have a problem when I run googleearth and compiz together. Basically GE will look very bad, like constant refreshing and the images are not rendered properly, they look like bad pixeled...
After a lot of googleing I was able to narrow this to be a problem with compiz and GE. If I turn visual effects off then GE runs fine. I think this might be because direct rendering is not on.

daniel@BlackBeauty:~$ glxinfo | grep direct
direct rendering: No (LIBGL_ALWAYS_INDIRECT set)

I am on Ubuntu 8.10 and my video card is:

daniel@BlackBeauty:~$ lspci | grep -i vga
lspci | grep -i vga
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)

Is there a fix for this?
A way of running GE without using desktop effects just for that application?
Or could I somehow enable direct rendering, and will that fix the problem?

My only workaround at the moment is to turn off visual effect whenever I want to run GE, but I hate this because it brings all my opened windows to the first workspace.
I remember in the days of Ubuntu 7.10 and 8.04 GE used to worked fine, so I assume direct rendering used to work fine as well.

Any help or pointers on how to fix this are much appreciated.

---

