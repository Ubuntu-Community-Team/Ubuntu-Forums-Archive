---
title: "Trying to connect to Wireless Internet"
date: 2009-04-03
forum: General Help
---

### Post by Sarah-Jane on 2009-04-03
Hi all
hope you can help

When I disable all security on my router I can connect, but as soon as I add my WEP key, I can't connect or it connects for literally 2 seconds and then disconnects. I've been trying for hours and read lots of advice, but to no avail.

Thanks in advance
Sarah-Jane

---

### Post by x22 on 2009-04-03
welcome to the forum

hmm:--sounds like a router setup problem to me.  We
have some pretty experienced router gurus around here:
what is the <make><model><version> please?  What
settings have you tried, for WEP?  64/128?  Are you
rebooting the router after the changes?

---

### Post by CyberMando on 2009-04-03
To me that sounds like a network-manager problem. There is another wireless manager called wicd that works very well.
sudo aptitude install wicd
will install it.

---

### Post by kilgore9 on 2009-04-04
yes I was struggling with this problem for a long time, trying all sorts of crazy stuff.  I installed wicd and was connected within 30 seconds...no more problems with the WEP key.

---

### Post by paradigm2 on 2009-04-04
> **Sarah-Jane said:**
> Hi all
hope you can help

When I disable all security on my router I can connect, but as soon as I add my WEP key, I can't connect or it connects for literally 2 seconds and then disconnects. I've been trying for hours and read lots of advice, but to no avail.

Thanks in advance
Sarah-Jane

WEP isn't all secure anymore anyway.  Does your router have the option to do WPA-PSK, WPA2-PSK (aka WPA-PERSONAL or WPA2-PERSONAL; psk stands for "pre-shared key) ?  If so try using that and also change the settigns in ubuntu.

---

