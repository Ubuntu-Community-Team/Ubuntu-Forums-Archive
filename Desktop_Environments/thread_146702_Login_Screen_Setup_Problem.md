---
title: "Login Screen Setup Problem"
date: 2006-03-18
forum: Desktop Environments
---

### Post by Johnyg on 2006-03-18
Few weeks ago I installed Ubuntu on my Pc, without the time to test it a bit. So now I began to configure it, install programs which I need and so on. I also installed KDE, but I'm using now Gnome. I write this because I think the problem has to do with the installation of KDE, but not sure. When I try to start the Login Screen Setup, I looks like something's loading, but after few moments, nothing happens. The same thing when trying to start the Login Screen Setup in KDE. Here's the log where the errors are displayed:

Mar 18 01:09:13 localhost gconfd (root-12825): starting (version 2.12.0), pid 12825 user 'root'
Mar 18 01:09:13 localhost gconfd (root-12825): Resolved address "xml:readwrite:/etc/gconf/gconf.xml.mandatory" to a writable configuration source at positio
Mar 18 01:09:13 localhost gconfd (root-12825): Resolved address "xml:readwrite:/usr/share/gconf/local.mandatory" to a writable configuration source at posit
Mar 18 01:09:13 localhost gconfd (root-12825): Resolved address "xml:readonly:/root/.gconf" to a read-only configuration source at position 2
Mar 18 01:09:13 localhost gconfd (root-12825): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position
Mar 18 01:09:13 localhost gconfd (root-12825): Resolved address "xml:readonly:/usr/share/gconf/local.defaults" to a read-only configuration source at positi
Mar 18 01:09:13 localhost gconfd (root-12825): Resolved address "xml:readonly:/usr/share/gconf/cdd.defaults" to a read-only configuration source at position
Mar 18 01:09:13 localhost gconfd (root-12825): Resolved address "xml:readonly:/usr/share/gconf/debian.defaults" to a read-only configuration source at posit
Mar 18 01:09:13 localhost gconfd (root-12825): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 7
Mar 18 01:09:43 localhost gconfd (root-12825): GConf server is not in use, shutting down.
Mar 18 01:09:43 localhost gconfd (root-12825): Exiting

So I thought the change of 'readonly' to 'readwrite' in the 'path' file would fix it, but it still doesn't work. Can someone tell me what is wrong and how to fix it ?

---

