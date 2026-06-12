---
title: "Gnome remote desktop rdp for multi-user environment / server"
date: 2023-03-29
forum: Desktop Environments
---

### Post by Pike_ on 2023-03-29
Does anyone know if it is possible to run gnome remote desktop headless with a direction to gdm login instead of needing an already logged in session?  I want to setup something equivalent to a Windows terminal server but the only option I see atm is to use Xrdp.

---

### Post by ActionParsnip on 2023-03-30
[https://www.digitalocean.com/community/tutorials/how-to-enable-remote-desktop-protocol-using-xrdp-on-ubuntu-22-04](https://www.digitalocean.com/community/tutorials/how-to-enable-remote-desktop-protocol-using-xrdp-on-ubuntu-22-04)

---

### Post by ActionParsnip on 2023-03-30
XRDP is great here. You don't need a logged in session

---

### Post by Pike_ on 2023-03-30
> **ActionParsnip said:**
> XRDP is great here. You don't need a logged in session

Unfortunately Xrdp is pretty terrible in real world remote situations from my experience -just re-tested it with all compression and color settings.  The actual RDP implementation of gnome remote desktop is great but I dont know why they focused on connected to an existing session instead of taking a more server based approach to it. 

There really doesn't seem to be a true open source remote desktop solution atm.  I hope the gnome team gets this working because they have a good start.

---

