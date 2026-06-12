---
title: "Xming connect hangs/blank screen before login, wireless only"
date: 2009-03-15
forum: General Help
---

### Post by alexwilsonphoto on 2009-03-15
I've set up 8.10 on an older machine, and I've run into problems trying to connect with Xming from my XP laptop to run a X Windows session.  When on wireless, the session appears to connect, but just shows the empty/blank checker screen with an x cursor.  No windows come up.  When I close Xming is says there are 0 clients connected.

If I connect the same computer via the LAN, I am able to run X session no problem, get the login screen, etc.

I don't have my wireless and wired connections set up any differently, both are DHCP, in the same IP range, etc.

Via wireless, I can connect with Putty, VNC, to a Samba share, etc. all no problem, just Xming has an issue.

I've looked at this thread, but it does not seem to be the same thing:
[http://ubuntuforums.org/showthread.php?t=325868](http://ubuntuforums.org/showthread.php?t=325868)
Disabling the clipboard does not help, adding KillInitClients=0 makes no difference.

Disabling the firewall on my XP machine makes no difference.

I've checked /var/log, and there's nothing added to any logs when a connection is attempted.

I've tried restarting the networking on the Ubuntu box in case something was cached, but it made no difference.

Any suggestions on what the problem might be, or any further step I can take to diagnose it?

---

