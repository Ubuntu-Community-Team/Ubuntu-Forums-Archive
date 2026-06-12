---
title: "Collecting login data on the network"
date: 2014-12-13
forum: Desktop Environments
---

### Post by Berduchwal on 2014-12-13
I have a local network at work with all PC ruining Ubuntu 14.04 desktop.
All PC have the same usernames and passwords. Not synchronised simply set up this way.
I need to set up a system which monitors who and when logs in to them. Logins are only local.
I already learned that I can see this information in: /var/log/auth.log
I would this information to be collected from the PC when they are on. 
Perhaps by some kind of Cron scrip and placed in a text file on one of the PC.

I have some little experience in writing scripts and I would like to do it alone but I would appreciate some guidance on the best way of doing this.

---

### Post by SeijiSensei on 2014-12-13
You can tell the logging daemon, rsyslog, to [write all its output to a remote server]("http://www.thegeekstuff.com/2012/01/rsyslog-remote-logging/").  Set up each client machine to log to a common server.

A better approach in the long run is to have authentication handled by a common server with LDAP or NIS.

---

### Post by Berduchwal on 2014-12-18
Thank you.

---

