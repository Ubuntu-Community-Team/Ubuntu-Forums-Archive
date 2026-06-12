---
title: "&quot;java java.net.SocketException: Permission denied&quot; exception in azureus when not root"
date: 2005-12-07
forum: General Help
---

### Post by weissed on 2005-12-07
Hi everyone,
Here it goes. I have installed jdk1.5 from Sun and Azureus.
I am facing a problem when running azureus from a non-root account. I am trying to set up Azureus to get inbound connections on a specific port (not used in the system) and I am getting "java.net.SocketException: Permission denied" when it tries to connect on that port.
If I run Azureus as root with gksudo, everything works fine. No exception.
So, normal user running java does not have priviledges to connect to localhost on a specific port... Does not make sense to me.
Anyone out there can enlighten me what could be the issue?
Cheers,
Edi

---

### Post by unnes on 2006-04-18
Did you install Azureus using Automatix? I think it's a problem with Azureus being installed into /opt/ instead of /home/ (which Automatix did for me too). If you uninstall Azureus and reinstall using the download from azureus.sourceforge.net to /home/, you should no longer have permissions problems.

---

### Post by weissed on 2006-09-08
My problem was caused by the fact that I wanted to use port 80 and in linux only root can connect to this port (all ports below 1000 I think)

So it was not related to azureus, or java. If you want to use the port forwarding on 80, you have to start it with root privileges.

---

