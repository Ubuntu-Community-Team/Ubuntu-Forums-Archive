---
title: "hylafax installation"
date: 2009-01-02
forum: General Help
---

### Post by michael.fries on 2009-01-02
Hello,

I have ubuntu 8.04, and a us robotics 0701 serial modem.  I am able to tell the modem to dial etc.  

My issue is with installing hylafax.  See following text:

mike@mike:/etc/hylafax$ sudo /etc/init.d/hylafax restart

sudo: unable to resolve host mike

 * Stopping HylaFAX faxq                                                 [ OK ] 

Not starting HylaFAX daemons since they are already running.

mike@mike:/etc/hylafax$ ps

  PID TTY          TIME CMD

15224 pts/0    00:00:00 bash

15300 pts/0    00:00:00 ps

mike@mike:/etc/hylafax$ sudo /etc/init.d/hylafax stop

sudo: unable to resolve host mike

 * Stopping HylaFAX faxq                                                 [ OK ] 

mike@mike:/etc/hylafax$ sudo /etc/init.d/hylafax start

sudo: unable to resolve host mike

Not starting HylaFAX daemons since they are already running.

mike@mike:/etc/hylafax$ sudo faxstat

sudo: unable to resolve host mike

Can not reach server at host "localhost", port 4559.

mike@mike:/etc/hylafax$ ps

  PID TTY          TIME CMD

15224 pts/0    00:00:00 bash

15465 pts/0    00:00:00 ps

In other words hylafax won't start up - it says it does, but it doesn't. (Or faxstat is lying)  Any ideas?

Thanks,
Mike

---

