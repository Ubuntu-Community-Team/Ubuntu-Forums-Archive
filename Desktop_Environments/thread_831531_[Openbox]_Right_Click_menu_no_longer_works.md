---
title: "[Openbox] Right Click menu no longer works"
date: 2008-06-16
forum: Desktop Environments
---

### Post by Totalchaos02 on 2008-06-16
I am not sure what I did exactly (I suppose I did it on accident and didn't notice I broke anything until awhile later) but my menu.xml reset and now when I right click the desktop my menu doesn't come up. Any ideas on how to fix this?

---

### Post by kerry_s on 2008-06-16
check your menu.xml?

---

### Post by urukrama on 2008-06-17
Which version of Openbox are you using? If you compiled the latest (3.4.7) from source, when you reconfigure Openbox it should display a dialog tell you where the error in your menu.xml or rc.xml file is.

If you use an earlier versions use an [xml validator]("http://www.validome.org/xml/") to check for errors (make sure you check the box that says "Well-formedness only").

---

