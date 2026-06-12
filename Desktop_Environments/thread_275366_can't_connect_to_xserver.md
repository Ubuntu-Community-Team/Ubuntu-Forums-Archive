---
title: "can't connect to xserver"
date: 2006-10-11
forum: Desktop Environments
---

### Post by joolz on 2006-10-11
Hi,
first time writer long time reader.

I have this problem, when i start an new xserver from my curren xsession

in xterm:
```
xinit -- :1
```

the server starts up ok but im unable to connect to it, i can't send any applications to it. This is the output from the xterm i started the xserver.

```

AUDIT: Wed Oct 11 15:29:22 2006: 3442 X: client 1 rejected from local host
Xlib: connection to ":1.0" refused by server
Xlib: No protocol specified

```

any ideas what could be wrong?

---

### Post by s_p_a_r_k_y on 2006-10-11
how are you sending programs there?
 DISPLAY=:1 program

?

---

### Post by joolz on 2006-10-11
```

xterm -display :1

```

for example

---

