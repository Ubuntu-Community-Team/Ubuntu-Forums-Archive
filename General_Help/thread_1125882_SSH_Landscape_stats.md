---
title: "SSH Landscape stats"
date: 2009-04-14
forum: General Help
---

### Post by prem1er on 2009-04-14
Where is the script located that is printing the system stats when I ssh into my machine.  I know the message is being redirected to /etc/motd, but where are those stats being generated?  Thanks.

---

### Post by lavinog on 2009-04-27
```

/etc/update-motd.d
/etc/cron.d/update-motd
/etc/update-motd.d/50-landscape-sysinfo
/usr/sbin/update-motd

```

---

