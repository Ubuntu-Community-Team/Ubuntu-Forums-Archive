---
title: "TTY defaults?"
date: 2010-07-07
forum: Desktop Environments
---

### Post by HyperFlexed on 2010-07-07
can anyone imagine a way to set certain TTY's to show specific programs upon login?

If I were to log in under my normal account, it'd be cool if I could set one up to load top upon authentication, maybe watch tail /var/log/syslog on another, and so on.

I know they require authentication, but would there be a way to say on startup if isTTY and TTYnum=y and if user=x execute script z?

---

### Post by sisco311 on 2010-07-07
> **HyperFlexed said:**
> 

I know they require authentication, but would there be a way to say on startup if isTTY and TTYnum=y and if user=x execute script z?



Edit the ~/.bash_profile file and at the bottom add something like:
```
if [ -z "$DISPLAY" ] && [ $(tty) = /dev/tty1 ]; then
  your_script_here
fi

``` 

To enable autologin on a virtual console (tty) install **rungetty**. Edit the /etc/init/tty1.conf file to something like:
```
# tty1 - getty
#
# This service maintains a getty on tty1 from the point the system is
# started until it is shut down again.

start on stopped rc RUNLEVEL=[2345]
stop on runlevel [!2345]

respawn
exec /sbin/rungetty tty1 --autologin **YOUR_USER_NAME**
```

---

