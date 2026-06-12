---
title: "Startup Order, Network, and Screenlet Startup"
date: 2010-02-06
forum: Desktop Environments
---

### Post by kendoori on 2010-02-06
Since last updates to 9.10 (now running 2.6.31-19-generic-pae) the startup of a screenlet that connects to the Internet for display of a web page no longer connects upon startup (e.g. can't display the web page). The screenlet is a python script that's part of the automatic startup programs (I'd added this to the Startup Applications preference applet). 

```

python -u /home/uname/.screenlets/Toodledo/ToodledoScreenlet.py

```

It acts the way that it acts if my machine has no internet connectivity. Assuming I let startup run its course and then immediately launch this screenlet manually, it connects with no issue.

I suspect that the updates somehow changed the order of when the network connects and that this is a timing issue.

Any recommendations on how to remediate this? Not real script saavy.

---

