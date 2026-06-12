---
title: "Re-build menu in Xubuntu?"
date: 2008-02-25
forum: Desktop Environments
---

### Post by Nu7a on 2008-02-25
Basically I upgrade my Xubuntu to 8.04 and now there seems to be some key thiungs missing from my settings and  system menus in the drop-down menu. Just wondering if theres maybe a way to have it re-build the menu list or what.

Thanks Tyler

---

### Post by ubuntu-freak on 2008-02-26
It's still alpha and buggy, so you're bound to have problems. I had a similar issue in Debian though, try;
 
**sudo apt-get update && sudo apt-get --reinstall install xubuntu-desktop**
 
or failing that;
 
**sudo apt-get dist-upgrade**
 
Nathan

---

