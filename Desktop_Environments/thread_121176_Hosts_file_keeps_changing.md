---
title: "Hosts file keeps changing"
date: 2006-01-24
forum: Desktop Environments
---

### Post by Westerberg on 2006-01-24
I use the hosts file available at [http://www.mvps.org/winhelp2002/hosts.htm](http://www.mvps.org/winhelp2002/hosts.htm) as a security/privacy measure.  It's just a matter of copying/pasting the contents into the /etc/hosts file.
On three occasions during the past week  the hosts file has been modified without my approval.  It requires root user permissions to write to, and no one uses this computer besides me.
In each case, all the 127.0.0.1 line prefixes were deleted, rendering the file useless as an ad-blocker.  Also, many of the lines were deleted altogether and my comp's name was deleted from the host name line.  
Can anyone explain how and why this could happen?

---

### Post by dcstar on 2006-01-24
[QUOTE=Westerberg]I use the hosts file available at [http://www.mvps.org/winhelp2002/hosts.htm](http://www.mvps.org/winhelp2002/hosts.htm) as a security/privacy measure.  It's just a matter of copying/pasting the contents into the /etc/hosts file.
On three occasions during the past week  the hosts file has been modified without my approval.  It requires root user permissions to write to, and no one uses this computer besides me.
In each case, all the 127.0.0.1 line prefixes were deleted, rendering the file useless as an ad-blocker.  Also, many of the lines were deleted altogether and my comp's name was deleted from the host name line.  
Can anyone explain how and why this could happen?[/QUOTE]
Yes, DHCP probably does it when you PC renews its details from a DHCP server.

---

