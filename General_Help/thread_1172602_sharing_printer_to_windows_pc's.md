---
title: "sharing printer to windows pc's"
date: 2009-05-28
forum: General Help
---

### Post by jnw222 on 2009-05-28
i have a hp deskjet (D1420) and need to have it so it is avaible to windows xp computers on my network?

---

### Post by munky99999 on 2009-05-28
[http://www.ubuntu.com/products/whatisubuntu/serveredition/features/fileprint](http://www.ubuntu.com/products/whatisubuntu/serveredition/features/fileprint)

These 2 features together will give you the option. Obviously you dont need server for it to work. Go into synaptic and get samba aka

sudo apt-get install samba smbfs

CUPS should be installed also... also named cups :)

Configuring samba to share the printer is in the configuration file: smb.conf

Fairly straight forward.

---

