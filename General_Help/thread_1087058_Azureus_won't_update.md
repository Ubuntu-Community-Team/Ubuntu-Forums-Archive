---
title: "Azureus won't update"
date: 2009-03-04
forum: General Help
---

### Post by Terminating.proprietary on 2009-03-04
I just downloaded Azureus, or what is now Vuze. It started updating as soon as it launched and keeps saying it needs to restart to install an update, but it has downloading nothing new. For some reason the update is not installing. I did some searching and there are plenty of similar problems but none sound like mine. Here is the output..

```

brian@brian-laptop:~$ azureus
file:/usr/share/java/Azureus2.jar ; file:/usr/share/java/swt-gtk-3.4.jar ; file:/home/brian/
changeLocale: *Default Language* != English (United States). Searching without country..
changeLocale: Searching for language English in *any* country..
changeLocale: no message properties for Locale 'English (United States)' (en_US), using 'English (default)'
Locale Initializing took 451ms
   Core: 43ms for Loading Plugin: azupnpav
   Core: 25ms for Loading Plugin: azupdater
   Core: 176ms for Loading Plugin: Built In
   Core: 251ms for Initializing Global Torrent Manager
   Core: 80ms for Initializing Plugin: Start/Stop Rules
   Core: 25ms for Initializing Plugin: Client ID
   Core: 25ms for Initializing Plugin: Distributed DB
   Core: 25ms for Initializing Plugin: Magnet URI Handler
   Core: 55ms for Initializing Plugin: LAN Peer Finder
Core Initializing took 855ms
   Core: 409ms for Initializing Plugin: Network Status
new shell took 254ms
skin init took 2996ms
MainMenu init took 351ms
createWindow init took 6ms
skin layout took 232ms
pre skin widgets init took 201ms
hooks init took 86ms
skin widgets init took 414ms
pre SWTInstance init took 0ms
SWTInstance init took 309ms
Activate tab tab-home took 169ms
sb=false
shell.open took 1602ms
processStartupDMS took 5ms
vuzeactivities init took 60ms
1236202548173:VuzeActivity] 237ms to paint 5 on redraw
DEBUG::Wed Mar 04 16:35:55 EST 2009::com.aelitis.azureus.core.crypto.VuzeCryptoManager$1::getPassword::151:
  Listener failed com.aelitis.azureus.core.crypto.VuzeCryptoException: Not Logged In on Creating online status key
    CryptoManagerImpl::getPassword::355,CryptoHandlerECC::createAndStoreKeys::667,CryptoHandlerECC::getMyPublicKey::587,CryptoHandlerECC::getPublicKey::297,BuddyPlugin::updatePublishSupport::1427,BuddyPlugin$18::runSupport::1395,AsyncDispatcher$1::run::84,AEThread2$threadWrapper::run::225
   Core: 35387ms for Loading Plugin: Built In

```


Hopefully someone out there knows what is going wrong.

---

### Post by Terminating.proprietary on 2009-03-04
ehhh and how can I post the output in the neat little box <code> doesn't work.

---

### Post by taurus on 2009-03-04
Instead of using < and >, replace it with [ and ].

---

### Post by Terminating.proprietary on 2009-03-05
bump

---

### Post by brunoscunha on 2009-03-08
I hve the same issue with vuze. I think it's a matter of user permitions, but my user has permitions enough or must i run vuze as root (i think that is pretty stupid)?

---

