---
title: "lircd won't start"
date: 2009-01-02
forum: General Help
---

### Post by bartvh on 2009-01-02
Yesterday I disconnected my remote control receiver and plugged it into another USB port.
Now, LIRC won't start anymore. I'm not sure if it's related, but I guess it must be.

Entering **/etc/init.d/lirc start** or **service lirc start** just gives me "starting lirc [fail]".
This is kind of frustrating. It's a useless message, I want to know why it won't start.

By googling I found out that lirc should log to syslog. However, /var/syslog contains nothing about LIRC.

I can manually start lircd. This apparently works, and it says so in the syslog. However, it's no real use because the correct info isn't given to it.

What can I do to locate this problem?

---

