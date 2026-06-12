---
title: "Networking problem"
date: 2006-07-09
forum: Desktop Environments
---

### Post by blue_shift on 2006-07-09
I connect to the internet using an ethernet connection to a modem. Usually this has been fine, and is detected/configured on booting. I installed and tried to set up firestarter, and succeeded in blocking access from kopete to various IM servers, despite trying to configure otherwise. Anyhow, I uninstalled firestarter and then ran ```

sudo iptables -P INPUT DROP
sudo iptables -P OUTPUT DROP
sudo iptables -P FORWARD DROP
sudo iptables -F
sudo iptables -X

```
under the impression it would flush iptables and leave the network functional. That session was okay, and network stuff worked. No I've logged on firefox and kopete can't find any address (host not found) so I assume the nameserver's being blocked? The same PC works on windows so it's not a hardware problem. Have I mis-configured iptables? Should I just re-install iptables?

Thanks.

Alex.

EDIT: Should of thought of that: I can't reinstall iptables without a network connection, can I?

---

