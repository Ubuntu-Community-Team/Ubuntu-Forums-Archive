---
title: "wxgtk2.6"
date: 2009-06-23
forum: General Help
---

### Post by _VWV_ on 2009-06-23
Dear All,


I need some help here. I'm trying to compile GENtle ([link]("http://gentle.magnusmanske.de/")). It seems like I have some problems with wxWidgets. The compilation goes fine, but if I lunch the program there's nothing there, just empty window with nothing written in it. The web site says that the program needs libwxgtk2.6-0 to work. I have libwxgtk2.8-0 installed on my system so I added libwxgtk2.6-0-dev and libwxgtk2.6-0 packages. But according to the output of configure script and according to the content of makefile that's generated, GENtle is compiled against libwxgtk2.8 on my system (which is quite expected, as version 2.8 is newer than 2.6). I want to try to compile it against libwxgtk2.6-0 (I think it might resolve the vxWidgets issue). How do I let configure and make scripts know that I want to use the older version (i.e. libwxgtk2.6-0) instead of libwxgtk2.8-0?

Thanks for your help in advance!

---

