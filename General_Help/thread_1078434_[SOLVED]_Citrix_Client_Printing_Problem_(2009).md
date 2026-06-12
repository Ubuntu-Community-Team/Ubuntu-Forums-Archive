---
title: "[SOLVED] Citrix Client Printing Problem (2009)"
date: 2009-02-23
forum: General Help
---

### Post by Treq on 2009-02-23
There is this archived thread that discusses how to get printing to work in Citrix: [http://ubuntuforums.org/showthread.php?t=454324](http://ubuntuforums.org/showthread.php?t=454324)

What worked well for me, instead of changing the location of printcap, was to make a symbolic link from /etc to the real file in /var/run/cups/printcap.

So steps involved were:
1. Stop CUPS: "/etc/init.d/cups stop".
2. Make the symbolic link: "ln -s /var/run/cups/printcap /etc/printcap"
3. Start CUPS again: "/etc/init.d/cups start".
4. Restart any running Citrix applications, if you have any running.

This seems to me a less invasive way getting Citrix to reach printcap.

Cheers,
Treq

---

