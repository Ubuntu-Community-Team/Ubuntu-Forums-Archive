---
title: "shadow the local session using NX"
date: 2009-05-19
forum: General Help
---

### Post by scandido on 2009-05-19
I'm trying to use FreeNX as a replacement for the functionality of VNC. Basically, I want a collaborator to be able to log in remotely and share the default session with the primary user. From what I've read, the way to do this is to enable certain flags 

ENABLE_MIRROR_VIA_VNC=1
ENABLE_DESKTOP_SHARING=1

in the file /etc/nxserver/node.conf and then connect using shadow from the client. (I'm using nxclient, FreeNX on the server.)

This seems to work but when I make the connection (from the client side), I'm able to manipulate the remote desktop (the server) but the view of the desktop does not update unless I resize the window (on the client). Has anyone run into this problem, or does anyone have any suggestions?

Thanks for you help.

---

### Post by bazbazbaz on 2009-08-03
Try disabling compiz on the server machine

---

