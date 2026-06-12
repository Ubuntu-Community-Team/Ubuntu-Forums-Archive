---
title: "root access?"
date: 2005-08-08
forum: Desktop Environments
---

### Post by tmasboa on 2005-08-08
how do you gain root access in the terminal.
I tried su 
but when i installed it, it never asked for a password for root.

---

### Post by bored2k on 2005-08-08
[QUOTE=tmasboa]how do you gain root access in the terminal.
I tried su 
but when i installed it, it never asked for a password for root.[/QUOTE]
 Ubuntu uses sudo.
[https://wiki.ubuntu.com/RootSudo?highlight=%28sudo%29](https://wiki.ubuntu.com/RootSudo?highlight=%28sudo%29)

---

### Post by charlieg on 2005-08-09
Do the following, using your own password when prompted:
```
charlie@localhost $ sudo -s -H
Password:
root@localhost $ echo "Now I'm root!"
Now I'm root!
```

---

### Post by tmasboa on 2005-08-09
thanks, now i can install stuff in console

---

