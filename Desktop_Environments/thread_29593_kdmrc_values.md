---
title: "kdmrc values"
date: 2005-04-25
forum: Desktop Environments
---

### Post by Storm Rider on 2005-04-25
A friend has noticed that several of the values in /etc/kde3/kdm/kdmrc , are not set at the default value even after a clean install. Why?

Example:
line 244
#allow root logins?
# default is **true** 
AllowRootLogin=**False**

---

### Post by SGC on 2005-04-25
I think the default values are KDE's defult values for KDM not Kubuntu's.

---

### Post by Firetech on 2005-04-25
The default value there is the KDE default. False is the kubuntu default, though.

---

