---
title: "Associate magnet links with azureus in firefox"
date: 2006-11-27
forum: Desktop Environments
---

### Post by jamespi on 2006-11-27
Hi, when i go to mininova and click on the azureus magnet links to download torrents, i get an error from firefox that says something like "firefox doesnt know how to open this address, because the protocol (magnet) isn't associate with any program"

im using dapper. any ideas how to associate the protocol with azureus?

---

### Post by jamespi on 2007-01-08
ok, here's how you do it [according to this page]("http://kb.mozillazine.org/Register_protocol#Linux_and_Mac").

    *  Type about:config into the address bar and press Enter.
    * Right-click -> New -> Boolean -> Name: network.protocol-handler.external.magnet -> Value -> true 
    * Right-click -> New -> String -> Name: network.protocol-handler.app.magnet -> Value -> /opt/azureus/azureus 
    * Ensure network.protocol-handler.expose-all is set to true. (mine was already)

make sure you have the right path to azureus (it's opt/azureus/azureus on my setup, because i used automatix to install azureus, but it might be something like /usr/sbin/azureus if the standard repo's are used perhaps?)

the way i checked (on edgy) was System -> Preferences -> Menu Layout

then i used the left panel to navigate to the internet menu, then right clicked azureus and chose properties. this shows the path to the executable.

---

### Post by epemac on 2008-01-15
A faster way to find azureus is to open a terminal and input "which azureus".

---

### Post by Acksys on 2008-03-23
Worked for me! Thanks for the tip.

---

### Post by fcastillo on 2008-07-07
Nice trick, I was wondering how can I use this method for other protocols, I've installed iTunes in wine and it's working fine, I'd like the itms protocol to be associated with an application

---

### Post by minhaaj on 2008-07-22
> **jamespi said:**
> ok, here's how you do it [according to this page]("http://kb.mozillazine.org/Register_protocol#Linux_and_Mac").

    *  Type about:config into the address bar and press Enter.
    * Right-click -> New -> Boolean -> Name: network.protocol-handler.external.magnet -> Value -> true 
    * Right-click -> New -> String -> Name: network.protocol-handler.app.magnet -> Value -> /opt/azureus/azureus 
    * Ensure network.protocol-handler.expose-all is set to true. (mine was already)

make sure you have the right path to azureus (it's opt/azureus/azureus on my setup, because i used automatix to install azureus, but it might be something like /usr/sbin/azureus if the standard repo's are used perhaps?)

the way i checked (on edgy) was System -> Preferences -> Menu Layout

then i used the left panel to navigate to the internet menu, then right clicked azureus and chose properties. this shows the path to the executable.
firefox doesn't know how to open the link. doesn't work for me. thanks anyways

---

