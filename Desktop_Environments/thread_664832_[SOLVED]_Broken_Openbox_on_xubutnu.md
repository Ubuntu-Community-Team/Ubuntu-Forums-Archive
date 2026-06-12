---
title: "[SOLVED] Broken Openbox on xubutnu"
date: 2008-01-11
forum: Desktop Environments
---

### Post by desper on 2008-01-11
Dear all,

Openbox suddenly cannot bring up any menu. both right click menu and middle click menu are gone, though the menu.xml and rc.xml of openbox seem good. The autostart.sh works well and hotkeys is also functioning. I cannot find the log of openbox bootup.

Please throw me some hints if you have same experienced.

---

### Post by yabbadabbadont on 2008-01-11
Please post the contents of the menu.xml and rc.xml files.

---

### Post by urukrama on 2008-01-11
Are you using Openbox within XFCE? If so, make sure XFCE does not control the desktop, as that will prevent Openbox from using the root menu.

If not, when did your menu stop working? If you have been editing something in your rc.xml or menu.xml, chances are something is wrong in either of these files. You can use an xml validator to check for errors. I use [this]("http://www.validome.org/xml/") one.

Also check your ~/.xsession-error file, and post the contents of that file here. It might contain some relevant information.

---

### Post by desper on 2008-01-12
The problem is solved. Nice hints! Thanks a lot.
There's a stupid careless mismatch of tag in the rc.xml, made by myself of course. The .xsession-error file clearly explains everything. I think there's no need to post rc.xml and menu.xml any more. 

Just feel obliged to say that OpenBox is such a nice WM. 

Thanks again and Good Day to you guys.

---

### Post by urukrama on 2008-01-12
Openbox is nice indeed!

I'm glad your problem is solved. You can mark this thread solved in the Thread Tools menu (above the first post, on the right).

---

