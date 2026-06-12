---
title: "Lost Vino options in 11.10"
date: 2011-10-18
forum: Desktop Environments
---

### Post by mrsuess2 on 2011-10-18
Several of the options for configuring vino have been lost in 11.10 (Oneiric Ocelot). For example, how can I cause Vino to listen on a port other than 5900? How can I cause Vino to only listen on localhost? It used to be the case than I could do this in the Vino preferences gui, then later it was moved to gconf-editor. However, now the options aren't available in either.

---

### Post by crdlb on 2011-10-18
You can find it in dconf-editor at desktop.gnome.remote-access . (I suspect that will change to something like org.gnome.Vino in a future release).

---

### Post by mrsuess2 on 2011-10-18
Perfect! crdlb, you are a Linux god.

---

### Post by keymanu on 2011-10-22
I just installed vino on lxde this morning, I set it to accept connections on port 5901. When I tried to connect from windows tightvnc it say's it can't connect to host, also my samba quit working as well, but ssh is working.

how is one affecting the other? If it is.

---

