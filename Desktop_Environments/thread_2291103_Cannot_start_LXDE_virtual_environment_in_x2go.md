---
title: "Cannot start LXDE virtual environment in x2go"
date: 2015-08-17
forum: Desktop Environments
---

### Post by Trey_Stanford on 2015-08-17
I am not sure what I need to do here. I have searched around online for about 30 minutes and turned up pretty much nothing. 

Anyways, I have set up a Lubuntu 15.04 installation to serve as a samba and VOIP server. I want to use x2go to do all remote maintenance and monitoring. I have all packages installed on the server that are necessary and have the client installed on my pc. I have attempted to start using LXDE, and that fails to execute, same story with startlubuntu, and startlxde.
/usr/bin/lxsession -s Lubuntu -e LXDE fails as well, they get suspended and when resumed are just a black screen. What command do I need to be using to execute the DE remotely????

---

### Post by Trey_Stanford on 2015-08-17
I get the following in the session log

```
Warning: Unrecognized session type 'unix-kde-depth_32'. Assuming agent session.
Warning: Failed to read data from the X auth command.
Warning: Generated a fake cookie for X authentication.
```

---

