---
title: "Command on boot"
date: 2005-12-11
forum: General Help
---

### Post by Anden008 on 2005-12-11
Hi..
I need to switch my wireless button on with the commands:
modprobe acerhk
echo 1 > /proc/drivers/acerhk/wirelessled

This has to be done at boot time, and before the network interfaces is set up.

Anyone knows where to do this? thx

---

### Post by TripHammer on 2005-12-11
Add that command to '/etc/init.d/networking' around line 84, like:```

case "$1" in
    start)
	doopt spoofprotect yes
        doopt syncookies no
        doopt ip_forward no

        modprobe acerhk
        echo 1 > /proc/drivers/acerhk/wirelessled

        log_begin_msg "Configuring network interfaces..."
        type usplash_write >/dev/null 2>/dev/null && usplash_write "TIMEOUT 120" || true
```

---

### Post by Anden008 on 2005-12-11
thx a lot.. it worked

---

