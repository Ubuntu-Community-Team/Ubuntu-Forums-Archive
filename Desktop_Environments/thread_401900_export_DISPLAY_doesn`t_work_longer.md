---
title: "export DISPLAY doesn`t work longer"
date: 2007-04-05
forum: Desktop Environments
---

### Post by schamane_ on 2007-04-05
Hi,

got a problem with my kubuntu box.

I want to export a Display to my box, but it won`t work

i do an xhost + on my box

the no-listen-tcp option is no longer in my conf
cat xserverrc
#!/bin/sh
exec /usr/bin/X11/X -dpi 100


i connect to the remote machine and do an

export DISPLAY=<ip>:0.0

than i start an program and it wont work

got anyone any idea what`s the problem

it was working a long time for me.

I think it`s since any X update.

regards

Schamane_

---

