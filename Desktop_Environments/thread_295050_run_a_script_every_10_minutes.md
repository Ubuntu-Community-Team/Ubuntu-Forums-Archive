---
title: "run a script every 10 minutes"
date: 2006-11-07
forum: Desktop Environments
---

### Post by hraposo on 2006-11-07
I want run a script every 10 minutes I created a file names dyndns em:
**/etc/cron.d**
An I put that line:
**0, 10, 20, 30, 40, 50 * * * * root /etc/ppp/ip-up.d/dyndns_update.sh >/dev/null 2>&1** But the script don't run every 10 minutes. Why?

---

### Post by wastrel on 2006-11-07
Try it without the spaces after the commas.

---

