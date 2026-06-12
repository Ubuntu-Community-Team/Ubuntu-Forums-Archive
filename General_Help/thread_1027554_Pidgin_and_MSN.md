---
title: "Pidgin and MSN"
date: 2009-01-01
forum: General Help
---

### Post by captaino on 2009-01-01
I am trying to log into msn messenger through Pidgin.  Everytime i try to login it says Connection Error from Notification Server. Unable to Connect.  So i had changed the server address from what was in there (messenger.msn.com) to messenger.hotmail.com.  Which is what the current server is for the Windows LIve messenger.  Still it wont Connect.  Any solutions?

---

### Post by Copernicus1234 on 2009-01-01
Just do some basic trouble shooting. For example:

$ **telnet messenger.hotmail.com 1863**
[I]Trying 65.54.239.80...
Connected to messenger.hotmail.msnmessenger.msn.com.akadns.net.
Escape character is '^]'.

Connection closed by foreign host.[/I]

If that doesnt work, I bet its a firewall in the way.

---

### Post by eotakos on 2009-02-03
i'm having the same problem and it is not a firewall problem for sure; i can use windows messenger from another computer behind the same router, and the system with the problem has no software firewall installed

---

