---
title: "Pidgin Proxy Authentication issue??"
date: 2009-02-23
forum: Desktop Environments
---

### Post by bmadaras on 2009-02-23
Using pidgin 2.5.2, and Ubuntu 8.10
Pidgin seems to be setup to use Gnome Network Proxy configuration by default, which is fine with me I like only have to change it in one place.  But it does not seem to use it properly, even though I manually setup the proxy information, and it does work in firefox, and setup the authentication with in the gnome proxy configuration I still get the below message when Pidgin tries to use the proxy, it does not seem to be adding the user and password for the proxy authentication. Should I have to add this someplace else?

(10:28:38) proxy: Proxy server replied with:
HTTP/1.0 407 Proxy Authentication Required
Proxy-Authenticate: Basic realm="Cisco Content Engine"
Content-Length: 381
Content-Type: text/html
Proxy-Connection: Close
(10:28:38) proxy: Connection attempt failed: Server closed the connection.

---

### Post by khc on 2009-02-24
you can do:

```

GNOME_DESKTOP_SESSION_ID= pidgin

```

to pretend you are not running GNOME and set the proxy directly in pidgin

---

