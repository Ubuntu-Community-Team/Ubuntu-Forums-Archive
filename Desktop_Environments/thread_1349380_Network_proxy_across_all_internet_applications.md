---
title: "Network proxy across all internet applications?"
date: 2009-12-08
forum: Desktop Environments
---

### Post by sav2005 on 2009-12-08
When will the Gnome Network Proxy setting become consistent across all applications so that users do not need to define proxies in Evolution and Synaptic as well as the Gnome Network Proxy? For anyone using a corporate laptop this is a complete bore and time waster.

---

### Post by sedawk on 2009-12-08
A workaround would be to install a local proxy, e.g.
something like squid or privoxy and then to direct all
applications to this local proxy.
If your real proxy changes you only have to change a
line in the configuration file of squid or privoxy and
to restart the squid or privoxy daemon.

There are many applications that have there own proxy
definition or ignore standards like the
environment variable http_proxy. Therefore a local
proxy might be the easiest solution.

---

