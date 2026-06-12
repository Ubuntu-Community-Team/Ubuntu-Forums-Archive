---
title: "Keeping X11 applications alive after SSH connection is lost or closed?"
date: 2011-07-20
forum: Desktop Environments
---

### Post by juliushibert63 on 2011-07-20
I'm forwarding an application (HandBrakegui) over an ssh tunnel using X11 forwarding as follows

ssh -C -p PORTNUM user@host -X ghb

This all works fine and X11 loads and handbrake's X11 output to my local mac. 

The server is Ubuntu 10.4 and the client is Mac OS X.

Is it possible for the X11 HandBrake Gui session to be kept alive once the SSH tunnel or the X11 window on the client (mac) has been closed? As I'm adding files to HandBrakes queue I want the programme to finish encoding them even if I turn off the client computer as the server is always on.

Is this possible?

---

### Post by enimeizoo on 2011-07-20
I don't think so. But if you are able to have it launched by something else than the ssh session (like with cron, I'm not sure, since I never actually used it), then you might be able to have it running even after the ssh tunnel is closed.

---

