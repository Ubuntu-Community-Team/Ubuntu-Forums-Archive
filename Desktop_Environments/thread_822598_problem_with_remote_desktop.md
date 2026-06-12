---
title: "problem with remote desktop"
date: 2008-06-08
forum: Desktop Environments
---

### Post by sparky333 on 2008-06-08
I'm at my wits end...
I'm trying to connect to my brother's PC using either krdc or vncviewer.
1. We are both running Ubuntu.
2. He has configured his System/Preferences/Remote Desktop screen
3. We have forwarded ports 5700,5800,5900 in his Actiontec Qwest modem.
4. When I try to connect to his ip_address:0, it hangs.
I can connect very nicely to another pc on my LAN, so I know I'm setup ok.
I just can't get to his pc across the internet.

Any help would be greatly appreciated!

---

### Post by hal8000 on 2008-06-08
Running any remote desktop requires more bandwidth than a modem, this is why you cant connect.
It works firn on your LAN, it will work acrosss the internet but only if both connections are DSL. I have connected from an 8Meg DSL connection to a 0.5Meg DSL, the remote connecetion could be accessed but was very slow.

Don't know exact bandwidth requirements but both computers will probably need a minimum of at least 0.5M connections at each end.

---

### Post by sparky333 on 2008-06-09
Thanks for your reply...

The Qwest Actiontec is a DSL modem.  He is running right around 2Meg.

---

