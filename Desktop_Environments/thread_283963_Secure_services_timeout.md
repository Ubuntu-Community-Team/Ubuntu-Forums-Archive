---
title: "Secure services timeout"
date: 2006-10-24
forum: Desktop Environments
---

### Post by the_billness on 2006-10-24
For some strange reason any "secure" service I attmept to connect to results in a timeout.

I have checked my netstat -tap and everything shows up fine.
I have no firewall installed.
I do have one https website that is working but its based on its own seperate compiled versions of apache 1.3x and openssl.
I have tried to reinstall using apt both with and without removal.
Format/Reinstall is not an option. (at least as little of an option as possible)

I'm just really at a loss.
Running Ubuntu Dapper Alt-Desktop (latest patches).

Any help would be greatly appreciated.

Thanks,
   Bill

---

### Post by AgenT on 2006-10-29
Try a different browser, such as mozilla (install pan with it). If it is just on secure websites than it is probably something with your browser configuration.

Also, try backing up your browser configuration folder/file. If you use mozilla or firefox, do this:
```
mv ~/.mozilla ~/.mozilla_backup
```
Now try using your browser to see if the same thing happens. To restore your settings do:
```
mv ~/.mozilla_backup ~/.mozilla
```

---

### Post by the_billness on 2006-10-30
Problem solved. For some reason one of the packages I installed added a drop all rule to iptables.

---

