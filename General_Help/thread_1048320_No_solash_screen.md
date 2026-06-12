---
title: "No solash screen?"
date: 2009-01-23
forum: General Help
---

### Post by mr_x408 on 2009-01-23
Hey guys... i was just wondering why i dont have a slpash screen on login, i had one yesterday but i accidentily unplugged my computer and now i dont. also when i type in my password i get 
"User's $HOME/.dmrc file is being ignored. This prevents the default session and language from being saved. File should be owned by user and have 644 permissions. Users $HoME/.drmc file must be owned by user and not writable to others"
any suggestions? im kindof new to ubuntu

---

### Post by derki on 2009-01-23
Do exactly what it says, use chown to change ownership and chmod to set rw privilegies for you to it.

---

