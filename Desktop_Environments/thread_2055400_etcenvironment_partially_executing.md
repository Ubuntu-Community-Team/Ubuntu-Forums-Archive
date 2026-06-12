---
title: "/etc/environment partially executing"
date: 2012-09-09
forum: Desktop Environments
---

### Post by johnelle on 2012-09-09
I am using xrdp as an alternative to the ummm "limited" desktop sharing included in Ubuntu 12.04.  I noticed it was properly setting up my environment so I added a . /etc/environment to /etc/xrdp/startwm.sh file.  It sets the path correctly but none of the other environmental stuff (like JAVA_HOME) get set.  After I am logged in I can issue . /etc/environment from a terminal window and everything is fine.  I've fiddled with this a bit but can't get this to work automagically.

Any suggestions?

---

### Post by youngunix on 2012-09-11
I'm not sure I understood the last part correctly, but what is the command that you are trying to execute automatically after logging in?

---

