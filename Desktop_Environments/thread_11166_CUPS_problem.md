---
title: "CUPS problem"
date: 2005-01-14
forum: Desktop Environments
---

### Post by filattiera on 2005-01-14
Goodmorning.

I have a problem with CUPS.

When I configure the printers that are on a printer server on my LAN (i.e. each printer has a IP and a port unique), the System configuration - > printers give me this:

Device URI: [http://192.168.1.57:0ps-hp4600](http://192.168.1.57:0ps-hp4600)

Id est, it add a "0" to the correct IP address.

I am not able to mange printer from web browser due to administration privilegies (please, help me also in this).

Help me.

thanks.
Luca.
 :sad:

---

### Post by hardcandy on 2005-01-14
"sudo passwd root" and create a root password. Log into CuPS with the username "root" and its password. Then try configuring your printers using cups.

---

