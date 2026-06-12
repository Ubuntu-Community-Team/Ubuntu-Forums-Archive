---
title: "changing icon in unity launcher in ubuntu 12.04"
date: 2013-09-29
forum: Desktop Environments
---

### Post by sandeep9285 on 2013-09-29
How can i change icon in unity launcher in ubuntu 12.04..Eg: how can i change the files icon displaying in the unity launcher in ubuntu 12.04??????

---

### Post by Isamu715 on 2013-10-02
Copy the relevant desktop entry from */usr/share/applications* to *~/.local/share/applications* (create this directory if it doesn't exist). Then right-click on the copied entry and select *Properties*. Click on the icon on the top left and select your new icon. Then reload Unity or log out and log bacnk in to your account. If the new icon is still not in the launcher unlock it from launcher and add it again.

---

