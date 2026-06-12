---
title: "lxterminal TERM variable"
date: 2010-11-26
forum: Desktop Environments
---

### Post by dovshap on 2010-11-26
I swtiched from kubuntu to lubuntu, and when I use konsole my TERM variable is set to "xterm", but in lxterminal it is set to "linux" which causes issues for me since I ssh into Solaris boxes for work.

I am trying to figure out where to set this because it is not in ~/.bashrc /etc/bash.bashrc, /etc/profile or ~/.profile.

Does anyone know where it is set, so I can modify it at the source?
Thank you

---

### Post by cavalier911 on 2010-11-27
```
user@lubuntu:~$ nano .bashrc
```

Add **TERM=xterm** to bottom.

```
user@lubuntu:~$ bash
```

or logout/in or reboot

---

### Post by dovshap on 2010-11-29
I thought it was going to be set somewhere else since it worked for me in konsole.
But I looked a little deeper and saw that konsole was setting the variable from it's profile environment settings. in ~/.kde/share/apps/konsole/Shell.profile.
So I added it to .bashrc, and that worked.

Thank You

---

