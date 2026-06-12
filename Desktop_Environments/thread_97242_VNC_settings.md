---
title: "VNC settings"
date: 2005-11-30
forum: Desktop Environments
---

### Post by rklauco on 2005-11-30
Greetings to all.

I am using two ubuntu boxes at home - one as TV/Video server and one as a usual workstation.

I would like to control the video box using VNC from my PDA.

Problem is, that on Windows Mobile I get only VNC viewer that supports protocol 3.3.

It seems to me that the Remote desktop option in gnome menu enables the vnc server (I can connect using realvnc client from the other box and from girlfriend's windows machine), but with different version (maybe 4, not 3.3).

Is there some way how to setup the protocol version to use?

...and one more thing at the end.
I was searching using "ps aux | grep vnc" for process like vncserver. I did not find any.
Neither I can find the vncserver executable on my box (only vncviewer and vncpasswd).
Anyhow, the vnc session is working :-)

Any help/sugesstions?

Thanks in advance.

---

### Post by cwaldbieser on 2005-11-30
[QUOTE=rklauco]Greetings to all.

I am using two ubuntu boxes at home - one as TV/Video server and one as a usual workstation.

I would like to control the video box using VNC from my PDA.

Problem is, that on Windows Mobile I get only VNC viewer that supports protocol 3.3.

It seems to me that the Remote desktop option in gnome menu enables the vnc server (I can connect using realvnc client from the other box and from girlfriend's windows machine), but with different version (maybe 4, not 3.3).

Is there some way how to setup the protocol version to use?

...and one more thing at the end.
I was searching using "ps aux | grep vnc" for process like vncserver. I did not find any.
Neither I can find the vncserver executable on my box (only vncviewer and vncpasswd).
Anyhow, the vnc session is working :-)

Any help/sugesstions?

Thanks in advance.[/QUOTE]

Gnome runs "vino" by default.
You can get other vnc servers from the repositories (just search for vnc).

---

