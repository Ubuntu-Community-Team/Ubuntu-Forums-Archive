---
title: "Auto-run commands at startup"
date: 2009-05-30
forum: General Help
---

### Post by sorfane on 2009-05-30
How would I get these commands to run at startup:
```

sudo iwconfig eth0 key s:passphrase
sudo iwconfig eth0 essid SSID
sudo dhclient eth0

```
?

Thanks very much.

---

### Post by Boondoklife on 2009-05-30
> **sorfane said:**
> How would I get these commands to run at startup:
```

sudo iwconfig eth0 key s:passphrase
sudo iwconfig eth0 essid SSID
sudo dhclient eth0

```?

Thanks very much.

Well that would depend on when you want it executed, but you could put it in rc.local or in you GUI's startup options.

---

### Post by sorfane on 2009-05-30
> **maletek said:**
> Well that would depend on when you want it executed, but you could put it in rc.local or in you GUI's startup options.
Well I'd preferably like them to run when the computer starts up, before login.

---

### Post by Yellow Pasque on 2009-05-30
You could use /etc/network/interfaces for that

```
iface eth0 inet dhcp
wireless-essid <SSID>
wireless-key <KEY>
auto eth0
```

---

### Post by ActiveFrost on 2009-05-30
Or you could make a shell script ( .sh ) & add it as a service ..

---

