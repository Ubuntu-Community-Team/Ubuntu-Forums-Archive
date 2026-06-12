---
title: "kdm: Don't start local X server"
date: 2008-07-23
forum: Desktop Environments
---

### Post by trojanfoe on 2008-07-23
Hi there, I am running Kubuntu 8.04 and want to stop kdm from starting the local X server and only allow sessions remotely via XDMCP.  I'm pretty sure the answer is in /etc/kde3/kdm/kdmrc, but cannot see an easy/elegant way to do it (I could replace the line "ServerCmd=/usr/bin/X -br" with something like "ServerCmd=/bin/true" but that seems a bit heavy-handed).

Anyone know the right way to do it?

Cheers,
Andy

---

### Post by trojanfoe on 2008-07-24
I've solved this myself through trial-and-error.  The method is to set "StaticServers" to nothing (""), instead of the default ":0", then kdm will no longer manage the (local) server.

Hope that helps someone...

Andy

---

### Post by trojanfoe on 2008-07-24
Oops - me again.  While this seems to have had the desired effect, it can hardly be called 'elegant' as it causes kdm_config to segfault, so I will keep trying...

---

### Post by trojanfoe on 2008-07-24
Sorted for sure now; simply set StaticServers= with no value, not even "".

I'll be quiet now...

---

