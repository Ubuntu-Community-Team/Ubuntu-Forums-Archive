---
title: "issue with mutter and libnvidia-tls"
date: 2011-05-18
forum: Desktop Environments
---

### Post by ramouz87 on 2011-05-18
Hi
I installed gnome3 and have issue letting it work:
when I try to run mutter i get the following error :

mutter: error while loading shared libraries: libnvidia-tls.so.260.19.26: cannot open shared object file: No such file or directory

but the installed version is libnvidia-tls.so.270.41.06
/usr/lib/libnvidia-tls.so.270.41.06
/usr/lib32/libnvidia-tls.so.270.41.06
/usr/lib32/tls/libnvidia-tls.so.270.41.06

when I run gnome-session i get this error:
gnome-session: symbol lookup error: /usr/lib/libcairo-gobject.so.2: undefined symbol: cairo_region_destroy:
when I run gnome-shell I get this error
gnome-shell: error while loading shared libraries: libgjs.so.0: cannot open shared object file: No such file or directory

anyone come across these error and solved them ?

Thanks in advance for help and suggestions.

Best,
Ramzi

---

