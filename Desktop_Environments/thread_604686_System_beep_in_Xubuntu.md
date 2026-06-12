---
title: "System beep in Xubuntu"
date: 2007-11-06
forum: Desktop Environments
---

### Post by Arkenzor on 2007-11-06
I know it is possible to totally disable the system beep in Ubuntu or Kubuntu, but I haven't been able to find an equivalent option in Xubuntu. Is there still a way to do it?


...

Well you know, my laptop's mighty 150dB beep of the doom is getting on my nerves...

---

### Post by tlayton_at_work on 2007-11-07
I use a login/start script with the following:]

```

#!/bin/sh
xset -b

```

---

### Post by Whiffle on 2007-11-07
I blacklisted the module 'pcspkr' on mine in /etc/modprobe.d/blacklist

---

