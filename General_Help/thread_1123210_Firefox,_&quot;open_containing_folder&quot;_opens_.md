---
title: "Firefox, &quot;open containing folder&quot; opens thunar, not nautilus"
date: 2009-04-11
forum: General Help
---

### Post by ad_267 on 2009-04-11
I'm using Ubuntu 8.10 with the Gnome desktop but also have XFCE installed. When I download a file and then right click and select "open containing folder" Firefox opens thunar instead of nautilus. Any idea on how to fix this?

---

### Post by ugkbunb on 2009-09-19
[http://rubylution.ping.de/articles/2007/09/11/open-containing-folder-in-firefox-under-linux](http://rubylution.ping.de/articles/2007/09/11/open-containing-folder-in-firefox-under-linux)

Basically navigate to about:config and create the following three:

network.protocol-handler.expose.file = true (Boolean)
network.protocol-handler.external.file = true (Boolean)
network.protocol-handler.app.file = nautilus (String)

---

