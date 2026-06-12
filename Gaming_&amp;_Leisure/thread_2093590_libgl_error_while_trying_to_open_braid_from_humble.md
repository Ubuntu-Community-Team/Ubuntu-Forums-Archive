---
title: "libgl error while trying to open braid from humble bundle"
date: 2012-12-11
forum: Gaming &amp; Leisure
---

### Post by nikhilbhardwaj on 2012-12-11
Hi,
I'm trying to play braid, this is a game that comes with the Humble Bundle for linux. When I start the game I get the following error
```
&#10140;  braid LIBGL_DEBUG=verbose ./braid
libGL: OpenDriver: trying /usr/lib/i386-linux-gnu/dri/tls/r600_dri.so
libGL: OpenDriver: trying /usr/lib/i386-linux-gnu/dri/r600_dri.so
libGL error: dlopen /usr/lib/i386-linux-gnu/dri/r600_dri.so failed (/usr/lib/i386-linux-gnu/libLLVM-3.1.so.1: symbol _ZNSt8__detail15_List_node_base7_M_hookEPS0_, version GLIBCXX_3.4.15 not defined in file libstdc++.so.6 with link time reference)
libGL: OpenDriver: trying ${ORIGIN}/dri/tls/r600_dri.so
libGL: OpenDriver: trying ${ORIGIN}/dri/r600_dri.so
libGL error: dlopen ${ORIGIN}/dri/r600_dri.so failed (${ORIGIN}/dri/r600_dri.so: cannot open shared object file: No such file or directory)
libGL: OpenDriver: trying /usr/lib/dri/tls/r600_dri.so
libGL: OpenDriver: trying /usr/lib/dri/r600_dri.so
libGL error: dlopen /usr/lib/dri/r600_dri.so failed (/usr/lib/dri/r600_dri.so: cannot open shared object file: No such file or directory)
libGL error: unable to load driver: r600_dri.so
libGL error: driver pointer missing
libGL error: failed to load driver: r600
libGL: OpenDriver: trying /usr/lib/i386-linux-gnu/dri/tls/swrast_dri.so
libGL: OpenDriver: trying /usr/lib/i386-linux-gnu/dri/swrast_dri.so
```

How can I fix this?
I am running a 32bit version of Ubuntu 12.10

For another game Crayon Physics Deluxe I get a similar error, but I'm not sure if they're the same thing
```
&#10140;  CrayonPhysicsDeluxe   LIBGL_DEBUG=verbose ./crayon 
libGL: OpenDriver: trying /usr/lib/i386-linux-gnu/dri/tls/r600_dri.so
libGL: OpenDriver: trying /usr/lib/i386-linux-gnu/dri/r600_dri.so
libGL error: dlopen /usr/lib/i386-linux-gnu/dri/r600_dri.so failed (/home/nikhil/opt/CrayonPhysicsDeluxe/lib32/libstdc++.so.6: version `GLIBCXX_3.4.15' not found (required by /usr/lib/i386-linux-gnu/libLLVM-3.1.so.1))
libGL: OpenDriver: trying ${ORIGIN}/dri/tls/r600_dri.so
libGL: OpenDriver: trying ${ORIGIN}/dri/r600_dri.so
libGL error: dlopen ${ORIGIN}/dri/r600_dri.so failed (${ORIGIN}/dri/r600_dri.so: cannot open shared object file: No such file or directory)
libGL: OpenDriver: trying /usr/lib/dri/tls/r600_dri.so
libGL: OpenDriver: trying /usr/lib/dri/r600_dri.so
libGL error: dlopen /usr/lib/dri/r600_dri.so failed (/usr/lib/dri/r600_dri.so: cannot open shared object file: No such file or directory)
libGL error: unable to load driver: r600_dri.so
libGL error: driver pointer missing
libGL error: failed to load driver: r600
libGL: OpenDriver: trying /usr/lib/i386-linux-gnu/dri/tls/swrast_dri.so
libGL: OpenDriver: trying /usr/lib/i386-linux-gnu/dri/swrast_dri.so
libGL error: dlopen /usr/lib/i386-linux-gnu/dri/swrast_dri.so failed (/home/nikhil/opt/CrayonPhysicsDeluxe/lib32/libstdc++.so.6: version `GLIBCXX_3.4.15' not found (required by /usr/lib/i386-linux-gnu/libLLVM-3.1.so.1))
libGL: OpenDriver: trying ${ORIGIN}/dri/tls/swrast_dri.so
libGL: OpenDriver: trying ${ORIGIN}/dri/swrast_dri.so
libGL error: dlopen ${ORIGIN}/dri/swrast_dri.so failed (${ORIGIN}/dri/swrast_dri.so: cannot open shared object file: No such file or directory)
libGL: OpenDriver: trying /usr/lib/dri/tls/swrast_dri.so
libGL: OpenDriver: trying /usr/lib/dri/swrast_dri.so
libGL error: dlopen /usr/lib/dri/swrast_dri.so failed (/usr/lib/dri/swrast_dri.so: cannot open shared object file: No such file or directory)
libGL error: unable to load driver: swrast_dri.so
libGL error: failed to load driver: swrast
```

It's a bummer to not be able to play these games.

---

### Post by pardalet on 2012-12-11
Take a look at this post: [http://ubuntuforums.org/showpost.php?p=12347678&postcount=5](http://ubuntuforums.org/showpost.php?p=12347678&postcount=5) (message #5 and onwards). I'd bet it's the same problem.

---

### Post by nikhilbhardwaj on 2012-12-11
Thanks buddy, That helped me solve it. It seems that the libraries aren't compatible and if we discard the ones that come with the game then it uses the ones that are provided by ubuntu and the game works!

---

