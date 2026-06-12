---
title: "Net Conf"
date: 2006-05-29
forum: Desktop Environments
---

### Post by g77s80 on 2006-05-29
Where can I manually edit the network configuration file in kubuntu
for some reason when I try to change the default gateway in system settings gui interface it just doesn't take (using root)
I can't connect to the internet without it
ThanX

---

### Post by nanotube on 2006-05-29
well, if you are up to tweaking stuff from commandline, you can edit the route settings with command "route", and add your gateway, etc.
"man route" for all the gory details.

---

### Post by vidak on 2006-05-29
/etc/network/interfaces?

---

### Post by fdoving on 2006-05-29
For permanent changes I suggest editing /etc/network/interfaces as vidak says. the 'route' command or the 'ip' command can be used to set the gateway manually, but it won't be permanent.

Go for /etc/network/interfaces

For more information:
```

man interfaces

```

- Frode

---

