---
title: "Ubuntu Breeze compatibility with RedHat9 HOW?"
date: 2005-11-15
forum: Desktop Environments
---

### Post by lisux on 2005-11-15
Hi all.
I have to use some propietary apps in my breeze box.
Mainly are animation packages like Maya or render engines like RenderMan.
The problem is that the version that i have of these apps are for redhat 7.3 and 9.0.
I have created two directories in /opt/redhat73 and /opt/redhat9 with the needed libs from this distros there, mainly libc and libstdc.
I run my apps from scripts that puts the LD_LIBRARY_PATH variable pointing to the corresponding redhat version directory.
The problems with the libstdc are solved, and the symbols with the libc too, because the apps loads the corrects libraries, the trouble comes with the dinamic linker, when i try to run an app i get this error:

pablo@casiopea:/opt/redhat73/opt/pixar/license-3.0$ LD_LIBRARY_PATH=/opt/redhat73/lib ./pixard
./pixard: relocation error: /opt/redhat73/lib/i686/libc.so.6: symbol _dl_starting_up, version GLIBC_PRIVATE not defined in file ld-linux.so.2 with link time reference

I have the corresponding ld library from redhat 73 in the directory pointed by LD_LIBRARY_PATH, but it seems that still use the ld library from the system.
How can i solve this problem?

Thanks

---

