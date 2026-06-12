---
title: "Help with apache2"
date: 2006-01-13
forum: General Help
---

### Post by tunafreedolphin on 2006-01-13
I screwed up my apache2 conf file(s). I have tried to do an apt-get remove and apt-get install apache2 but this does not recreate the conf file(s). Could someone please post the default file or tell me where I can get it. Thanks

---

### Post by Koybe on 2006-01-13
To remove a program AND the config file you need to 
```
apt-get --purge remove apache2
```
Unfortunatly I do not have the original file as i'm on fedora right now.

---

