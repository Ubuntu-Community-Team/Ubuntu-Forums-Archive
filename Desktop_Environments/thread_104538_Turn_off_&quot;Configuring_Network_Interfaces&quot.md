---
title: "Turn off &quot;Configuring Network Interfaces&quot; at boot?"
date: 2005-12-16
forum: Desktop Environments
---

### Post by grsing on 2005-12-16
Is there any way to tell Ubuntu not to run the "Configuring Network Interfaces" part at boot (and also not to sync the clock, since that won't work without the network)?  It's just kind of a pain to have to wait for it to time out when you know you're not connected to the internet.  If you need my hardware, I'll tell you, but I wouldn't think it matters.  Thanks!

---

### Post by ape on 2005-12-16
Rather than turn off networking, install the ifplugd package. This is a much more usable method for those times that you don't have network connection.

---

### Post by grsing on 2005-12-16
Thanks, that is a much better solution.

---

### Post by linkunderscore on 2005-12-16
Also, this doesn't solve the problem but it does prevent you from having to wait for it at boot "Crtl-C"

---

