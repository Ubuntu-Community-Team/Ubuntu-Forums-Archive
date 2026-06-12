---
title: "remastersys and cupsd"
date: 2009-01-03
forum: General Help
---

### Post by romeyde on 2009-01-03
i used remastersys to move my system to a new box and a ssd drive.  everything went very well and was extremely happy with the results until I realised my printer is no longer working.   the cupsd daemon dies with this:

 Jan  3 19:00:01 ubuntu1 cupsd: Unable to read configuration file '/etc/cups/cupsd.conf' - exiting!

the conf exists and permissions look fine.  i've tried reinstalling pretty much every cups package that is currently installed with no change.  

anyone else had this issue and know what the resolution is?  printing prior to remastersys worked fine.

---

### Post by romeyde on 2009-01-03
after hours of messing with it, i finally resolved the issue, didn't realise cups had it's own error log in /var/log/cups.   saw this there:

E [03/Jan/2009:19:19:32 -0500] "/etc/cups/ssl/server.crt" is a bad symlink - No such file or directory
E [03/Jan/2009:19:35:33 -0500] "/etc/cups/ssl/server.key" is a bad symlink - No such file or directory

just deleted those symlinks and the daemon was happy.

---

