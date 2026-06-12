---
title: "GNOME's support for keymap table switching"
date: 2009-03-08
forum: Desktop Environments
---

### Post by henryz21651 on 2009-03-08
Xorg 1.5 and above provides input device hotplug support, which involves
keymap table switching for new device plugged in. However GNOME does not
seem to support such keymap table switching, it does not respond to X 
server's MappingNotify event (by doing another round of key grabbing).  
Is there any plan on the way to add this support ?

---

