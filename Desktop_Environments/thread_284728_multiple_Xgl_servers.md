---
title: "multiple Xgl servers"
date: 2006-10-26
forum: Desktop Environments
---

### Post by wilk on 2006-10-26
I can run beryl on Dapper and a GeForce FX 5200, using the 
```
# Override display 1 to use Xgl (DISPLAY 1 IMPORTANT FOR ATI FGLRX).

0=Xgl

[server-Xgl]

name=Xgl server

command=/usr/bin/Xgl :0 -fullscreen -ac -accel glx:pbuffer -accel xv:fbo

flexible=true

```

lines in gdm.conf-custom.

But when I start a new server, with gdmflexiserver or switchuserapplet, no choice is offered and I get the good old X server, so goodbye beryl. I thought the whole point of the "flexible = true" option was to allow the gdmflexiserver to use the server it is applied to.

---

