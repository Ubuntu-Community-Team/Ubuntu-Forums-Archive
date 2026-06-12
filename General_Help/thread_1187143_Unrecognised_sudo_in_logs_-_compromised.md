---
title: "Unrecognised sudo in logs - compromised?"
date: 2009-06-14
forum: General Help
---

### Post by risingsun on 2009-06-14
Hi, I was just browsing my logs when I noticed an unrecognised use of sudo in the auth logs. Is this a system thing or should I be concerned?

Jun 14 12:07:25 SYSTEMNAME sudo:     root : TTY=unknown ; PWD=/ ; USER=USERNAME ; COMMAND=/usr/bin/gconftool --get /system/http_proxy/use_http_proxy
Jun 14 12:07:25 SYSTEMNAME sudo:     root : TTY=unknown ; PWD=/ ; USER=USERNAME ; COMMAND=/usr/bin/gconftool --get /system/http_proxy/host
Jun 14 12:07:25 SYSTEMNAME sudo:     root : TTY=unknown ; PWD=/ ; USER=USERNAME ; COMMAND=/usr/bin/gconftool --get /system/http_proxy/port

I'm very worried by this since I don't recall any use of sudo around that time by myself. is anyone able to tell me what this does and if I should be concerned?

Edit: The only thing I noticed that's different from typical sudos is that it's as root, not as myself and that the home directory is /. Would this suggest it is a system thing? I've found five other counts of it.

---

### Post by jimv on 2009-06-15
Do you have an SSH server installed?

---

### Post by geirha on 2009-06-15
It's one of the system's anacron scripts.

```
grep 'sudo' /etc/cron.daily/*
```

I get the same log messages. Nothing to worry about.

---

