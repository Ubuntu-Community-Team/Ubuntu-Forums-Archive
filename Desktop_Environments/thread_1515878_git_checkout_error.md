---
title: "git checkout error"
date: 2010-06-23
forum: Desktop Environments
---

### Post by tapas_mishra on 2010-06-23
I am running following command which is giving error

```

git clone git://git.kernel.org/pub/scm/linux/kernel/git/trovalds/linux-2.6.git linux-2.6
Initialized empty Git repository in /home/tapas/LKP/pandora/linux-2.6/.git/
fatal: The remote end hung up unexpectedly

```
Some one suggested me to check my firewall I am not clear as which port does git uses.
Can some one tell what is wrong in above command.
Ubuntu 9.04

---

### Post by nilarimogard on 2010-06-23
Most probably the port is closed by the ISP. Use a proxy for GIT and it should work.

---

### Post by tapas_mishra on 2010-06-23
I could not understand your reply use proxy for git how ?

---

### Post by nilarimogard on 2010-06-23
See [here]("http://www.webupd8.org/2010/03/how-to-get-git-working-behind-firewall.html")

---

