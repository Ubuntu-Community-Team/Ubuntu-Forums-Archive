---
title: "access files on partition"
date: 2008-12-20
forum: General Help
---

### Post by windowsfree on 2008-12-20
How can I access the windows files from my WUBI installation.  I don't understand how I can, but I had someone told me it was possible, but did not remember the method.

Is it possible and if so, please point me in the correct direction.

Thanks

---

### Post by pytheas22 on 2008-12-20
If you installed using wubi, you should be able to find your Windows files under the /host directory on Ubuntu.  Click the Places menu in the top-left of your screen, then select to open your Home Folder (or any other location really...we just need to open up a file browser window).  After it opens, type '/host' in the address bar.  And you should see the root of your C:\ drive in Windows.  Does it work?

Note that you may need to be root in order to modify the files inside /host.  But you should be able to read them as a normal user.

---

