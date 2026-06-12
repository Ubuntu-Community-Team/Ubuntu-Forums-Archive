---
title: "can I send my X session to a foreign X server (7.04) ?"
date: 2007-06-02
forum: Desktop Environments
---

### Post by light333 on 2007-06-02
Hi,

I want to send my *whole* X session (desktop and everything) to a foreigh X server.

Can I do it (Ubuntu 7.04) ?

I thought of changing to init level 3 and then run something like "startx -display x.x.x.x:0" where
x is the IP of my foreign X server... but I didn't even manage to go to init level 3 because of the upstart
(no inittab file) and later I thought that xstart probably doesn't accept a '-display" param because it isn't
an X app, but an X server...

thanks
light.

---

