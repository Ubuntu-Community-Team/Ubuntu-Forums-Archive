---
title: "X crashes after some minutes"
date: 2005-08-22
forum: Desktop Environments
---

### Post by kubix on 2005-08-22
Hello.
I have been experiencing some problems with X and Gnome lately. For some unknown reason, sometimes when I log into Gnome it crashes after a few seconds or minutes. The only useful information I get from /var/log/syslog are the following lines:

```
Aug 22 15:16:53 localhost gconfd (kubito-7383): Received signal 15, shutting down cleanly
Aug 22 15:16:53 localhost gconfd (kubito-7383): Exiting
Aug 22 15:16:53 localhost gdm[6110]: gdm_slave_xioerror_handler: Fatal X error - Restarting :0
``` 
Then GDM restarts, I log back and sometimes everything goes fine, and sometimes it crashes again after some time.

---

