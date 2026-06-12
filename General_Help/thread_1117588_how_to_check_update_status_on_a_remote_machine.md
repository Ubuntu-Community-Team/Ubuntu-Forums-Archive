---
title: "how to check update status on a remote machine?"
date: 2009-04-06
forum: General Help
---

### Post by fduff on 2009-04-06
it's straightforward when connected in front on your Ubuntu distro, you get notified of new updates by the *update manager* icon showing. But how can you check the update status of a remote machine, with only remote shell (SSH) no VNC?

thanks.
F.

---

### Post by terrorsathan on 2009-04-06
Type "sudo apt-get update" and then "sudo apt-get upgrade" to retrieve updates.

Best regards

---

### Post by kpkeerthi on 2009-04-06
You could also do [X over SSH]("http://www.vanemery.com/Linux/XoverSSH/X-over-SSH2.html")

---

### Post by fduff on 2009-04-06
actually I meant to check the update status (i.e. system up to date, needs update etc) from the CLI.

from looking into apt-get help, the closest I've found seems to be:

```
~$ sudo apt-get upgrade -u
```

where it can tell you if the system requires any updates

output:
```
Reading package lists... Done
Building dependency tree
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

means system up to date.

---

### Post by kpkeerthi on 2009-04-06
You should still run ```
sudo apt-get update
``` prior to running ```
sudo apt-get upgrade -u
```

---

