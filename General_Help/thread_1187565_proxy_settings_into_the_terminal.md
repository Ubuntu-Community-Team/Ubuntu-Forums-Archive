---
title: "proxy settings into the terminal"
date: 2009-06-14
forum: General Help
---

### Post by The-ITu on 2009-06-14
hey people,  i already know how to put the proxy setting into firefox and synaptic, but im just wandering is there i was i could do that in the terminal?

---

### Post by acovrig on 2010-08-25
there is other posts now, google it and the second one is a good one, it ises gcoftool to set the settings, also `man gconftool` helps.  try `gconftool -s /system/http_proxy/host -t int <server ip-address>` and/or `gconftool -s /system/http_proxy/port -t int <server port>` and/or `gconftool -s /system/proxy/mode -t string manual` and/or `gconftool -s /system/http_proxy/use_http_proxy -t bool true`

---

