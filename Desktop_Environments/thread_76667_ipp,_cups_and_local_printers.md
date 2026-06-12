---
title: "ipp, cups and local printers"
date: 2005-10-15
forum: Desktop Environments
---

### Post by jesi on 2005-10-15
Hello,

I just installed the hp printer driver and set it up using their instructions.  Now im not quite sure why the ipp port is listening for connections when I run netstat.  This is a local printer:

tcp        0      0 localhost.localdoma:ipp *:*                     LISTEN
tcp        0      0 localhost.localdo:34262 localhost.localdoma:ipp ESTABLISHED
tcp        0      0 localhost.localdoma:ipp localhost.localdo:34262 ESTABLISHED

Is this normal or should I redo my printer install?  Oh yes, when I stop the cupsys service I can't view the printers I have installed.  It says the server is not running under system->admin->printing

Thanks,
Jesi

---

### Post by jesi on 2005-10-15
Well since I can't delete my own post here, I'll just reply with the solution.

I port scanned my ip address rather than locahost and that worked fine.  The port is closed to the outside and open to local programs.

Jesi

---

