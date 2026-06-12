---
title: "Can't install Enemy Territoru"
date: 2005-10-29
forum: Gaming &amp; Leisure
---

### Post by vondur on 2005-10-29
When I try and run the setup file, it fails with this error message:

[INDENT]root@dhcp107-90:/home/mevans/Desktop# ./et-linux-2.55.x86.run
Verifying archive integrity... All good.
Uncompressing Enemy Territory 2.55...........................................................................................................................................................................................................................................................................................................
/root/.setup11605: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory
./setup.sh: line 143: 11629 Segmentation fault      "$setup" "$@" 2>>$NULL
The setup program seems to have failed on x86/glibc-2.1[/INDENT]
It looks like it need glibc2.1, where does one get this?

Thanks for any help
matt

---

### Post by jeffreyvergara.NET on 2005-10-29
you can try using synaptic's search

---

