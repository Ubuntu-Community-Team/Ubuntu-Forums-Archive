---
title: "Wine text does not appear!"
date: 2008-02-08
forum: Desktop Environments
---

### Post by jackkerouac on 2008-02-08
For some reason, after installing Wine Doors, none of the text in any wine program appears. Take a look at the images attached. I have tried reinstalling Wine, uninstalling Wine Doors, all to no avail. Any help would be greatly appreciated.

---

### Post by kryth on 2008-02-08
If you can access to a Windows install, you can try coping all of your fonts from there into your ~/.wine/drive_c/windows/fonts directory. That may or may not do it.

---

### Post by kryth on 2008-02-08
or better yet:

sudo apt-get install msttcorefonts

---

### Post by jackkerouac on 2008-02-08
I uninstalled Wine, Wine Doors and then compiled Wine from scratch and that seemed to fix it. Thanks.

---

