---
title: "apt with and without proxy"
date: 2008-12-19
forum: General Help
---

### Post by Joe of loath on 2008-12-19
Hi,

I have ubuntu on a portable hard drive, and use it at school (with a proxy) and at home (without). At school the updates and repositories worked first time, but when I got home it doesn't work at all, and keeps telling me 'it can't resolve "proxy" (which is the name of the proxy)'. I can't seem find any configuration files to edit (and possibly create a script to switch between the two.)

can anyone help?
thanks,
Joe

---

### Post by dcstar on 2008-12-20
> **Joe of loath said:**
> Hi,

I have ubuntu on a portable hard drive, and use it at school (with a proxy) and at home (without). At school the updates and repositories worked first time, but when I got home it doesn't work at all, and keeps telling me 'it can't resolve "proxy" (which is the name of the proxy)'. I can't seem find any configuration files to edit (and possibly create a script to switch between the two.)

can anyone help?
thanks,
Joe

System-Administration-Synaptic-Preferences-Network.

---

### Post by Aearenda on 2008-12-20
Or look in /etc/apt/apt.conf if it exists.

---

### Post by Joe of loath on 2008-12-20
ok, there are no proxy settings in synaptic (ie the boxes are greyed out), but it still asks for one. apt.conf doesn't extist, or at least didn't last time I checked. I'll reboot and see later.

---

### Post by Aearenda on 2008-12-20
Also have a look at /etc/apt/sources.list - it is possible to hard code the proxy name in there too. And, check system->preferences->Network Proxy for a system-wide setting.

---

