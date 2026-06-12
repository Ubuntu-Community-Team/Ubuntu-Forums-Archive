---
title: "Could not export display"
date: 2005-12-14
forum: Desktop Environments
---

### Post by arsya on 2005-12-14
Currently I am having problem exporting display.

I already did xhost + in my laptop.
Then I telnet to the server and export DISPLAY=<mylaptopip:0.0>
then when I ran the application, nothing appears in my laptop.

This kind of problem happened to me when I was using Mandrake but I found out that the security level and the firewall prevent me for exporting display. So, when I disabled or lowered the security level and disable the firewall, I could do the export display.

But in ubuntu, I don't think I have the firewall installed.
So, perhaps there's a configuration, in Gdm or X that I should change in order to make it work?

Could someone help me with this problem?

---

### Post by kaamos on 2005-12-14
I had this problem with ssh, and it was just because my /etc/ssh/ssh_config was not set to allow x11-forwarding. So try looking if telnet has similiar configuration files.

I hope this helps a little.

---

