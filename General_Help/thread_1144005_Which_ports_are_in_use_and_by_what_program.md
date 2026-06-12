---
title: "Which ports are in use and by what program?"
date: 2009-04-30
forum: General Help
---

### Post by tenmilez on 2009-04-30
Is there an easy way to figure out what ports my server is using and what program/service is associated with them?

---

### Post by prem1er on 2009-04-30
Run a port scan on your machine.  There are web apps for this [http://www.t1shopper.com/tools/port-scanner/](http://www.t1shopper.com/tools/port-scanner/), as well as standalone apps.

---

### Post by sedawk on 2009-04-30
Your are looking for command line tool "lsof" (list open files).
But you need to be root to have the required permissions.

To look for processes listening on ports use:
```

sudo lsof |grep -i listen

```

The file /etc/services maps port numbers to names, so output
like this 
TCP *:ssh (LISTEN)
means something is listening on port 22, the ssh-port.

---

### Post by Brandon Williams on 2009-04-30
```
sudo netstat -lp --tcp --udp
```

This will listen just the listening tcp and udp ports with an indication of the service number for the port (if known) and the process. If you want unix domain socket listeners too (i.e. local only), then take out the --tcp and --udp flags to see all listeners.

---

