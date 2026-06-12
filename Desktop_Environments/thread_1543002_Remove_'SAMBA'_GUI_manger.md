---
title: "Remove 'SAMBA' GUI manger"
date: 2010-07-31
forum: Desktop Environments
---

### Post by duiu on 2010-07-31
I want to remove only the GUI Samba manager that shows up in System -> Administration -> Samba. I installed this along with the smbd and samba suite and I just want the GUI gone, I believe it is interfering with some custom items I added to smb.conf.

What package do I need to remove?

---

### Post by Morbius1 on 2010-07-31
> **system-config-samba**

I think that's the only one that will add the "Samba" menu item under Administration.

You can always run the following command to make sure that's the right package:
```
gksu system-config-samba
```

---

