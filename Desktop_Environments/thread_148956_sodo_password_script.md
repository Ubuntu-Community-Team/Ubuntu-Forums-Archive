---
title: "sodo password script"
date: 2006-03-23
forum: Desktop Environments
---

### Post by terranz on 2006-03-23
A while ago I found
```
sudo eject ipod
```

What I want to know is can I write a script that does not require a person to type in the password.

I put a script on my desktop to eject my ipod but I don't want my wife having to click 'run in terminal' and then typing in a password.

---

### Post by noob_Lance on 2006-03-23
open the terminal... and type

sudo visudo

edit it like such

{user}   All=NOPASSWD: /path/to/script


save and exit. and a quick restart and your set :)

---

