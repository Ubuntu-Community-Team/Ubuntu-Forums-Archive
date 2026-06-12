---
title: "Remmina issues in Ubuntu 12.04 Win Server 2008"
date: 2013-06-05
forum: Desktop Environments
---

### Post by Broco on 2013-06-05
Hello,

when connecting to a Windows 2008 Server via Remmina (RDP) the program keeps freezing upon succesful login. This only occurs if I have the security option set to either "RDP" or "TLS".
When I kill the program ("killall remmina" or "kill -9 PID") and restart remmina and then login the existing session its fine, that means login into a running session is no problem, but as soon as I log out normally on the remote-desktop the same happens again.

When security is set to "negociate" everything is fine but the problem then is that Remmina asks to accept the server certificate every time which is quite annoying for our users and then the Windows-Login-screen doesn't appear, just the one from remmina.

Tried different remmina versions now (even downloaded and installed the Debian debs) but still the same issue.
Any hints?

Greetings

Broco

---

