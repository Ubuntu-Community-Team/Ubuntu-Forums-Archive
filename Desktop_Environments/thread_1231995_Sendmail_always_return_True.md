---
title: "Sendmail always return True"
date: 2009-08-05
forum: Desktop Environments
---

### Post by satish_j on 2009-08-05
On my Ubuntu system,I have disabled the sendmail service to start manually through admin-->services window.
Now,when iam trying to send mail through a simple php script,it always return true even when the sendmail service is not running.
nmap command confirms that port 25 is not open.
when i start sendmail manually,port 25 gets opened.
Can some one help me as to why sendmail always return true.PHP documentation says that 'true means the mail is accepted for delivery'.
Also,the script takes a long time to execute and finally returns 'true' every time.

---

