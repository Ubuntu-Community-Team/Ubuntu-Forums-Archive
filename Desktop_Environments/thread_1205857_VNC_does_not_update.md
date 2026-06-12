---
title: "VNC does not update"
date: 2009-07-06
forum: Desktop Environments
---

### Post by bvdvzw on 2009-07-06
I tried to get remote destop working. The server & client machines are running ubuntu 9.04. I get the connection up and running, then I get a copy on the client machine, but this doesn't update. Although I see the mouse moving on the server machine. I can also type there, but the client image does not update. Anybody idea's?
Thanks,
Bruno.

---

### Post by pwilliams on 2009-09-18
I am having the exact same issue.  I've played around with network settings and I don't believe it has to do with ports getting blocked.  Additionally I've tried both realvnc and tightvnc from a windows client and have had the same issue.

---

### Post by pwilliams on 2009-09-18
Found the solution.  This appears to be related to an issue occurring with redhat as well:
[https://bugzilla.redhat.com/show_bug.cgi?id=214446](https://bugzilla.redhat.com/show_bug.cgi?id=214446)

The trick is to disable desktop visual effects.

Goto System -> Preferences -> Appearance

Goto Visual Effects Tab

Select None.  Vnc should immediately start updating correctly on the remote client.

---

