---
title: "Login returns to login"
date: 2018-06-22
forum: Desktop Environments
---

### Post by bw4linux2 on 2018-06-22
Hey everyone,

I'm not new to Ubuntu, but I'm not a power-user exactly. I upgraded from 14.04.1 to 18.04 (bad idea). As of now, I cannot login to any DE except plain Gnome, the rest all just go back to login. Also, I have to boot using the previous kernel or the system won't boot. 

I have tried removing .Xauthority, moving .config and .local, reinstalling the DEs. Nothing has worked. And it seems every time I do login, it gives me initial setup dialog or whatever, but my settings seem intact.  I haven't been able to find anything in logs. Display manager logs are either empty or plain don't exist.

---

### Post by Xian on 2018-06-24
Do you still have upstart package installed?

If so:

[COLOR=#000000]```
sudo apt remove upstart --purge
```[/COLOR]

---

