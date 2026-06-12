---
title: "NX Server and x11vnc"
date: 2006-11-26
forum: Desktop Environments
---

### Post by mrbarletta on 2006-11-26
Hi all!,

this is a mental note for everybody trying to setup free nxserver and x11vnc or trying to login remotely in their desktops. 

In edgy, if you install x11vnc, nxserver will fail to start the session without a propper error message.

If you want, as i did, login remotely to your machine in a secure fashion and then use the normal(shared using vino) desktop, your setup will look like:

1) NX Client -->  NX Server 
2) NX Server Launch vncviewer application (note that using the vnc function of nx client may work, but usually doest not work as expected)
3) vncviewer --> localhost:0 

Good luck!

---

