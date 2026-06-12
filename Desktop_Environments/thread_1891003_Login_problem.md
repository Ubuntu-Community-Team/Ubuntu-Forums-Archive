---
title: "Login problem"
date: 2011-12-04
forum: Desktop Environments
---

### Post by BriannNL on 2011-12-04
Dear all,

After hours of Googling and trial and error, I'm at a loss right now.

Suddenly I wasn't able to login to Ubuntu anymore. It kept saying that my password was incorrect. Also, I wasn't able to change my password in recovery mode. After many attempts, I finally found out that /etc/pam.d/common-password contained some weird data. (it looked like a disclaimer/about file from libatasmart.git, how this could get suddenly here, I don't have a clue at all)

So, I took this file from the live CD of Ubuntu 10.04 (my version is 11.10) and replaced the strange one. After this, my password was accepted. Still, I can't get into Ubuntu. It gives the following errors when I try to login via a terminal (ctrl+alt+f4):

bash: $'\037\213\b': command not found
FATAL: Error inserting pppoe (/lib/modules/3.0.0-13-generic/kernel/drivers/net/pppoe.ko): Operation not permitted
bash: /usr/sbin/pppd: Access restricted
bash: exec: Cannot execute /usr/sbin/pppd: Access restricted

And than it asks for the credentials again.

I have checked the permissons of those files and they turned out to be correct. I've also tried to temporarily rename pppoe.ko, but with no effect. At last I've tried to disable pppoe via blacklist.conf, but with no effect. Starting an older kernel of Linux doesn't help either.

Could somebody please help me with this?

Thanks in advance!

Kind regards from The Netherlands,

BriannNL

---

