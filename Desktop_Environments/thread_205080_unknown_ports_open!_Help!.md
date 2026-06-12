---
title: "unknown ports open! Help!"
date: 2006-06-27
forum: Desktop Environments
---

### Post by ubiwankanubi on 2006-06-27
when using the network tools I see the following ports in state LISTEN
tcp 127.0.0.1 33094 LISTEN
tcp 127.0.0.1 631 LISTEN
tcp 127.0.0.1 42456 LISTEN
and a few other tcp/udp ports...

but when running netstat -l

none of those ports are showing as LISTEN.

anyone know what those ports are? and how to close them?

---

### Post by johnc4510 on 2006-06-27
I know that cups listens at 631, but I'm not sure about the other 2

---

### Post by johnc4510 on 2006-06-27
Further research shows port 33094 as being used by Apache, and port 42456 as being used by Evolution.

---

### Post by ubiwankanubi on 2006-06-28
how did you find which progs were using those ports? I'm still rather a beginner so I might not know about these possibly simple thngs.

Also, I don't have apache installed...

---

