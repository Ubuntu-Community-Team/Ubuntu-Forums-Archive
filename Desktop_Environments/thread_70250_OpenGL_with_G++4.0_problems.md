---
title: "OpenGL with G++4.0 problems"
date: 2005-09-29
forum: Desktop Environments
---

### Post by nathan43081 on 2005-09-29
When I compile an opengl app wtih g++4.0 I get the folowing error:

/usr/bin/ld: warning: libstdc++.so.5, needed by /usr/X11R6/lib/libGLU.so, may conflict with libstdc++.so.6

Having libstdc++.so.5 linked in gives me problems with the list class of the STL library so I really want libstdc++.so.6. Is there anything that I can do to get this changed. I have tried simlinking libstdc++.so.5 to libstdc++.so.6, but this just caused a bunch of problems. I think that the library that needs libstdc++.so.5 is xlibmesa-glu. I am not sure of this, but so far as i can tell this is the offender.

Thanks for any help.

Nathan

---

