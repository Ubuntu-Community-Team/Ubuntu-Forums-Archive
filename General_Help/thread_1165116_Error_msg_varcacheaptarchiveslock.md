---
title: "Error msg /var/cache/apt/archives/lock"
date: 2009-05-20
forum: General Help
---

### Post by DoricMan on 2009-05-20
Trying to get adobe Flash for BBC web pages I get the following error messsage.

E: Could not get lock /var/cache/apt/archives/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the download directory

The lock location /var/cache/apt/archives/lock appears to be present.

Can anyone help?

Thanks DM.

---

### Post by geirha on 2009-05-20
Another APT application is running. Only one should run at the same time, so the first one to run, locks all others out. Check that you are not already running synaptic, add/remove..., update-manager, aptitude or anything like that.

---

