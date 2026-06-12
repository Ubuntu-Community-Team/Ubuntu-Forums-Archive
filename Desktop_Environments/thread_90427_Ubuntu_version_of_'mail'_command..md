---
title: "Ubuntu version of 'mail' command."
date: 2005-11-14
forum: Desktop Environments
---

### Post by holiday on 2005-11-14
In my old fedora installation I had a little cron script that checked my external ip and then emailed me if it changed. This was useful if I was on the road and wanted to check my server - and my ISP had changed my ip. Which now and then it does quite regularly unless I pay another some number of dollars more a month. 

I could always get my external ip from my mail.

In that script I used the 'mail' program

mail -s "ip change" [email]me@myemailaddress.com[/email]

But Ubuntu doesn't have it. Does anyone know how to get that program or if there is an alternative.

---

### Post by dcstar on 2005-11-15
[QUOTE=holiday]In my old fedora installation I had a little cron script that checked my external ip and then emailed me if it changed. This was useful if I was on the road and wanted to check my server - and my ISP had changed my ip. Which now and then it does quite regularly unless I pay another some number of dollars more a month. 

I could always get my external ip from my mail.

In that script I used the 'mail' program

mail -s "ip change" [email]me@myemailaddress.com[/email]

But Ubuntu doesn't have it. Does anyone know how to get that program or if there is an alternative.[/QUOTE]
Install "mailx" from Synaptic.

---

