---
title: "Allowing www-data to start program"
date: 2017-02-26
forum: Desktop Environments
---

### Post by t00by1 on 2017-02-26
I'm trying to get some home automation to work from an ubuntu desktop.

Currently I can recieve a web-request, have PHP parse it and for example tell an USB-IR-sender to start my TV, set the correct input and allow me to use my ubuntu on the livingroom tv. But I want to add to this functionality. 
For example, start specific programs (Kodi in this case).

At the moment I've tried to connect via SSH to my ubuntu box and run the command
```
DISPLAY=:0 sudo -u tobias /usr/bin/kodi &

```
This actually works well, kodi starts on the correct display and works as it should, but my problems arise when I try to get the user running the web-server to do this.
How do I allow www-data to start kodi as the user tobias?

---

### Post by t00by1 on 2017-02-26
Turns out this was easier than I thought!

I've added 
www-data ALL=(tobias) NOPASSWD: /usr/bin/kodi
using
sudo visudo

This made it possible to start kodi from my webserver. :)

---

