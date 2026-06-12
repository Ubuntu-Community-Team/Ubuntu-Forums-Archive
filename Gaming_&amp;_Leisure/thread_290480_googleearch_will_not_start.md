---
title: "googleearch will not start"
date: 2006-11-01
forum: Gaming &amp; Leisure
---

### Post by plaporte on 2006-11-01
I just installed googleearth on my new 6.10 Ubuntu.

When i start it, i get the following message

plaporte@plaporte-desktop:~$ ./googleearth
[sis_tex.c:100]: Failure to allocate texture memory.
plaporte@plaporte-desktop:~$

after a successfull Initialissation, Connection to the server and Loading of myplace....

Probably not enough memory.

Any help would be appreciated.

Tks

---

### Post by MrBlond83 on 2006-11-01
If I'm not mistaken, google earth requires direct rendering. Make sure you have it enabled by doing a "glxinfo | grep direct".

---

### Post by plaporte on 2006-11-01
I used your  glxinfo | grep direct   and the reply is; direct rendering: Yes

So I am still stuck here... no GoogleEarth.

Pierre

---

