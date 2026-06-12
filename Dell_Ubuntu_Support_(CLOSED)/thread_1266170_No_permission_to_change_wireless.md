---
title: "No permission to change wireless"
date: 2009-09-14
forum: Dell Ubuntu Support (CLOSED)
---

### Post by jmstern on 2009-09-14
I have a Dell Inspiron, with Ubuntu version 8.10.   I was browsing just fine, when all of a sudden, the wireless dies.  I went into the network config, and I am unable to modify, create or delete a wireless config. (have 2 locations, one for the house, one for starbucks.)

Is there a snazzy command whereby i can fix the permissions so that I can access the configs, and hopefully access the network again, without re-installing?

---

### Post by epicoder on 2009-09-14
Type this in a bash terminal: gksudo nm-connection-editor

This will run the Network Connections dialog as the administrator.

---

