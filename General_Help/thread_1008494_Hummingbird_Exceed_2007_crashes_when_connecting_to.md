---
title: "Hummingbird Exceed 2007 crashes when connecting to Ubuntu 8.10"
date: 2008-12-11
forum: General Help
---

### Post by planetjeff on 2008-12-11
Hello all,
My work environment currently has a series of Solaris and Redhat systems.  We commonly use Hummingbird Exceed 2007 to connect remotely to these systems, with no problems.  I am trying to see if we can use Ubuntu, but immediately after selecting the Ubuntu system to connect to, the Exceed program immediately crashes.  I've even enabled the logs and nothing on the Exceed side indicates a problem.

I initially selected the Ubuntu 8.10 server edition, then realized it does not come with X capability.  Now I'm using Ubuntu 8.10 desktop.  This is installed on a Dell PowerEdge 2850.  The install went fine and I've enabled remote login, but it consistently crashes Exceed.

Anyone else have this problem or know what could be causing this issue?  If we can't solve this we won't be using Ubuntu, obviously.

Thanks,
jeff d.

---

### Post by planetjeff on 2008-12-11
Figured it out!

I found a reference on the Hummingbird forum:
> Using XDMCP Broadcast to access server desktops....  Use to be able to access all servers, with little xconfig medaling.  migrated to new XP machine and problems. Can get to red hat servers usually.  Some Solaris 9 systems.  Can't access any solaris 10 servers.  Seems to be hit and miss. No the firewall is not on?  Any idea on what i might try to get this woking.

 Thanks

Accepted Answer

The problem is with the X Server Protocol Extensions (XConfig):

Removing XINERAMA fixed it.  The tech also suggested removing RANDR, but that was not an issue.


I tried disbling both, and as it turns out the RANDR option was the one causing the crash.  So right now I have XINERAMA enabled, but not RANDR, and I can now login remotely to Ubuntu using Exceed XDMCP.  YMMV!

---

