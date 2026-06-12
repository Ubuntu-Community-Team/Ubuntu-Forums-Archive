---
title: "starting system log daemond freeze"
date: 2006-10-25
forum: Desktop Environments
---

### Post by hraposo on 2006-10-25
My system stop when boot and appears the **starting system log daemond**. I don't use X because the computer is a server. How I stop this daemond on boot?

---

### Post by tigerstripedcat on 2006-10-25
You say you don't use X, but if you have it installed use "bum" -- "boot up manager"
If not...

it's in /etc/init.d/sysklogd

check out:

man update-rc.d

---

### Post by captaindave on 2006-10-26
I installed a Dlink G650+ card and aircrack yesterday and now have the same problem. System hung up on re-boot and now just hangs when booting 6.06 LTS at * Starting System log ....

I can startup in recover mode, but don't know what to do next. Any suggestions?

Thanks...

Cap'n Dave

---

