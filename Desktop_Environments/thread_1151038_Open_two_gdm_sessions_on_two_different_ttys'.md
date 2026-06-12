---
title: "Open two gdm sessions on two different ttys'?"
date: 2009-05-06
forum: Desktop Environments
---

### Post by Desrik on 2009-05-06
Ok now, I know I can open another gdm session on display :1 by going to tty2 and running ```
sudo gdm start :1
``` but how can I make this happen on startup? An even better thing would be if I could start that on startup and have it automatically connect as a secure remote connection to my home server. Possible in any way?

---

### Post by theDaveTheRave on 2009-05-07
Desrik

there is a thread out there on setting up "multiheaded" systems (single terminal with 2 monitors, keyboards, mice).

it sounds like that may have what you are after.

regarding an auto login to your home server... you could potentially write a scripts to start up VNC, but I wouldn't know how to get it to start on a given tty.

I know it isn't very helpfull in the first instance, but hopefully it will give you a point in alternative directions.

David

---

