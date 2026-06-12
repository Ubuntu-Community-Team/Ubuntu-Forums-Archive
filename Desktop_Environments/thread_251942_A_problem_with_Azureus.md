---
title: "A problem with Azureus"
date: 2006-09-06
forum: Desktop Environments
---

### Post by Rhapsody on 2006-09-06
After a lot of work, I've finally got Azureus up and running (also getting the latest beta version to fix the annoying pop-up problem).

However, everytime Azureus starts, it tells me that "azplugins/Tracker Static Pages,Tracker Dynamic Pages,IRC" needs updating to 2.1.1_CVS. By itself, this is not a problem. But once it downloads and tries to apply the update, I get a pop-up saying

"Version 2.1.1_CVS of plugin 'azplugins' failed to install - /home/rhapsody/.azureus/plugins/azplugins/azplugins_2.1.1.jar (Permission denied)"

Of course, this means that the update is not installed, so Azureus asks me again after I restart it, and keeps asking over and over because it can't install the update.

Aside from this, it seems to finally be working OK, but it'd certainly be nice if I could install updates.

---

### Post by FryerFox on 2006-09-06
As a first step, you might want to verify that you have read/write permissions for the appropriate folders:

/home/rhapsody/.azureus/plugins/etc/etc

and

/opt/azureus, or wherever you put the binary

---

### Post by Rhapsody on 2006-09-06
> **FryerFox said:**
> As a first step, you might want to verify that you have read/write permissions for the appropriate folders:

/home/rhapsody/.azureus/plugins/etc/etc

and

/opt/azureus, or wherever you put the binary
How do I check that though? The folder in /home isn't visible in Konqueror, though I wrote the Azureus2.jar file to /usr/share/java myself (using a sudo cp command).

---

