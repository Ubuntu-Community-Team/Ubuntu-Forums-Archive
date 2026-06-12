---
title: "FTP Server Issue"
date: 2009-01-15
forum: General Help
---

### Post by Barnicle on 2009-01-15
Our company has a backup that is FTP'ed off-site nightly. We haven't had any issues with it until recently. After some troubleshooting, it seems that when trying to connect to the off-site server, either FTPS (client) is not connecting or the server isn't. The thing is, we are able to connect to the server using Filezilla and successfully transfer files. We have checked all the possibilities with our script to ensure it's not the problem.

We are using SSH logins when connecting to the server directly through Filezilla and Putty. That is the only issue I can think of that might be not letting the batch file connect through FTPS. Could SSL be the issue? Are there any other reason that might cause FTPS and the server not connect?

---

### Post by Barnicle on 2009-01-16
We restarted the off-site server, and it seems to have fixed the issue. It might have been a caching issue, or it just needed a reboot??

---

### Post by fiatguy85 on 2009-01-16
I'm not an expert, but I've had issues like that where rebooting fixed the problem.  Another thing you can try if it happens again is to try restarting the individual services related to the problem on the server to narrow it down using the invoke-rc.d command.  Then you might be able to determine which is causing the issue and go from there.

---

### Post by Barnicle on 2009-01-16
I will give it a whirl. Thanks.

---

