---
title: "After upgrade to Jaunty printing broken for Vista-&gt;ubuntu"
date: 2009-04-28
forum: General Help
---

### Post by bboons on 2009-04-28
Before upgrade to ubuntu I was able to install the HP5610 printer (USB attached to Ubuntu) from Vista simply by Searching for the printer on the network. After upgrade to Jaunty I'm unable to print, I tried deleting the printer from Vista and tried search again but this time it could not find the printer. I tried reinstalling the printer from Jaunty and it did not help.
Nothing has changed on my network or the Vista laptop. The only thing that changed was the upgrade to Jaunty.
I enabled debugging and looked at /var/log/cups/error_log and did not observe any activity while searching for the printer from Vista.
I did see some messages:
I [28/Apr/2009:20:34:44 -0400] Listening to 0.0.0.0:631 on fd 13...
I [28/Apr/2009:20:34:44 -0400] Listening to :::631 on fd 14...
I [28/Apr/2009:20:34:44 -0400] Listening to /var/run/cups/cups.sock on fd 15...
I [28/Apr/2009:20:34:44 -0400] Resuming new connection processing...


Is this ok for it to be listening on 0.0.0.0 ?

Please help.
Thanks

---

### Post by bboons on 2009-04-29
Let me answer my own question:
After adding this line to cupsd.conf, things started working again.

...
<Location/>
# Allow shared printing...
Order allow,deny
**Allow From 192.168.0.***
Allow all
</Location>

I basically added the line in **bold**. I thought that the *Allow all* statement should have worked, but for some reason I had to explicitly specify my LAN as an allowed entity.

---

