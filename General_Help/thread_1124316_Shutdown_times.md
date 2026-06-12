---
title: "Shutdown times?"
date: 2009-04-13
forum: General Help
---

### Post by solwic on 2009-04-13
I'm trying to find out what time my PC was last shut down.  Can this be done?  I know Windows stores the shutdown date and time in the registry, but I can't find anything similar in Ubuntu.

Thanks for any help.

---

### Post by solwic on 2009-04-13
I found this:  ```
last -x|grep shutdown | head -1
``` but it doesn't give any output.

EDIT:  Nevermind, I found it.  For those interested, the information is in /var/log/syslog.  I don't know a fancy command to scan for last shutdown time (I searched it manually, the info was near the top), but the information is in there (at least in Ubuntu 8.10).

Thanks anyway. :)

---

### Post by drs305 on 2009-04-13
> **jrock612 said:**
> EDIT:  Nevermind, I found it.  For those interested, the information is in /var/log/syslog.  I don't know a fancy command to scan for last shutdown time (I searched it manually, the info was near the top), but the information is in there (at least in Ubuntu 8.10).

Thanks anyway. :)

On my computer, a normal shutdown is accompanied by an entry in syslog of "exiting on signal 15". Yours may be similar. Find your shutdown or reboot message and then substitute it in this command:
```

cat /var/log/syslog | grep "*exiting on signal 15*"

```

---

### Post by Cybie257 on 2009-04-13
> **jrock612 said:**
> I found this:  ```
last -x|grep shutdown | head -1
``` but it doesn't give any output.

EDIT:  Nevermind, I found it.  For those interested, the information is in /var/log/syslog.  I don't know a fancy command to scan for last shutdown time (I searched it manually, the info was near the top), but the information is in there (at least in Ubuntu 8.10).

Thanks anyway. :)


cat syslog | grep restart

Where restart, use your keyword. Since I haven't shutdown my computer for quite sometime, I was only able to verify with 'restart'. :)

-Cybie

---

### Post by northern lights on 2009-04-13
There's several exit codes, the most common being 15. If you filter the syslog contents for "exiting on signal", you should find what you're looking for:```
cat /var/log/syslog | grep "exiting on signal"
```

---

