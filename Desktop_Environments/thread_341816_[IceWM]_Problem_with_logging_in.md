---
title: "[IceWM] Problem with logging in"
date: 2007-01-19
forum: Desktop Environments
---

### Post by Alz on 2007-01-19
I installed IceWM using apt-get, but when I try to log in using it, it freezes. Once I get back to the login screen, and I try again, it says errors occurred last time. When I check the xsession errors file, it says "IceWMBG: error while loading shared libraries libimlib.so.1 file not found." I already installed the liblmlib package, and the dev one as well just in case, but I still cant log in using IceWM. :(  Any one have a solution? Thanks in advance. :D

Some info:
Ubuntu latest version
128MB RAM
10GB HD
Dell Latitude CPx

EDIT: I fixed it by changing my "/etc/environment" file to also point to "/usr/local/lib," where the libimlib file was. Strangely enough, when I did a locate, those files didn't show up.

---

