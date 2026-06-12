---
title: "Firefox can't resolve host names?"
date: 2005-06-24
forum: Desktop Environments
---

### Post by IchBin on 2005-06-24
I can't browse with FF because it cannot resolve host names. I have no idea why. I can ping sites like google.com from the terminal. I can't browse to the page by the host name, but if I type the IP address in I can browse to the site just fine. Anyone know what I need to change to fix this? FF is set to automatically connect to the internet. I've even tried the auto detect proxy settings. I can't figure this out for the life of me...Any help is greatly appreciated. Firefox is the only thing that don't work. Konquerer works just fine with host names.

---

### Post by nictuku on 2005-06-24
I guess you should disable all proxy settings and double check your dns settings. 

That's an odd behaviour.

---

### Post by IchBin on 2005-06-24
I found another post where a guy turned off ipv6 and rebooted. I did that and everything works great now. Why would that be screwing firefox up?

---

### Post by The Na Kun on 2005-06-24
[QUOTE=nictuku]I guess you should disable all proxy settings and double check your dns settings. 

That's an odd behaviour.[/QUOTE]
 Yeah, it's probably dns server settings.  Hey, IchBin, atleast you can connect to the internet..

---

### Post by wylfing on 2005-06-24
It's a disconnect between Firefox on Ubuntu requesting that names be resolved to IPv6 addresses by default and modems/routers that don't support IPv6. Such modems and routers choke on this request to serve up an address in IPv6 space. If you type in a numeric address like 68.115.71.53 then you are already in IPv4 space and nobody chokes. Try typing an IPv6 address into your address bar and marvel at how it does not resolve  ;-)

By the way, you do NOT have to reboot your computer every time you make a configuration change. That is how the poor saps in Windows-land live. The way to make Firefox behave is:
1. Type about:config in the Firefox address bar.
2. Type network.dns.disableIPv6 in the Filter box.
3. Double-click the network.dns.disableIPv6 entry to change it from false to true.

Done! There is no need to restart anything, including Firefox. You're good to go.

---

