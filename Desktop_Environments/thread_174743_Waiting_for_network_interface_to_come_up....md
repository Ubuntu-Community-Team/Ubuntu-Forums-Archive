---
title: "Waiting for network interface to come up..."
date: 2006-05-12
forum: Desktop Environments
---

### Post by linuxNewb on 2006-05-12
When I installed breezy I was using eth0 (ethernet). I am now using eth1 (wireless) instead.

Now when I boot-up without an ethernet cable plugged into eth0, when it gets to: 

Waiting for network interface to come up...

It breaks out of the pretty graphics thing, and switches to the full screen white text on black background, then waits about 30 seconds before moving on. This is really annoying. Is there a way for me to skip this, or let it know to use eth1 instead?

Thanks in advance.

---

### Post by louis_nichols on 2006-05-12
Yes. first, when it hangs at boot time, press Ctrl+C to skip that step. Then, after logging in, go to System>Administration>Networking, choose eth0, click properties and uncheck "enable this connection". This way it won't be started at boot time anymore.

---

### Post by linuxNewb on 2006-05-13
That worked great. Thank you.

---

### Post by 0MG on 2006-05-13
[QUOTE=linuxNewb]That worked great. Thank you.[/QUOTE]

Wow, it's amazing that you can get by on 256 **KB** of ram nowadays. How is that working for you?;)

---

### Post by louis_nichols on 2006-05-13
[QUOTE=0MG]Wow, it's amazing that you can get by on 256 **KB** of ram nowadays. How is that working for you?;)[/QUOTE]
pmpl! that's a good one!

---

