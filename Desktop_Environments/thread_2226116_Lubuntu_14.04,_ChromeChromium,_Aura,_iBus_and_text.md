---
title: "Lubuntu 14.04, Chrome/Chromium, Aura, iBus and text entry"
date: 2014-05-25
forum: Desktop Environments
---

### Post by vasa1 on 2014-05-25
Lubuntu 14.04 users (and others) who installed Chromium 34 from the software center reported problems with text entry: [https://bugs.launchpad.net/ubuntu/+source/chromium-browser/+bug/1307648](https://bugs.launchpad.net/ubuntu/+source/chromium-browser/+bug/1307648)

I didn't see the problem with Google Chrome 34 (not Chromium). It seems that, for whatever reason, Chromium 34 (from the software center) had Aura enabled whereas Google Chrome 34 did not.

Now Chrome 35 ships with Aura and the text entry problem exists. The workaround is to open a terminal and run```
ibus exit
```. I noticed the problem with Google Drive when I tried to edit documents and spreadsheets.

---

### Post by vasa1 on 2014-05-26
According to [https://code.google.com/p/chromium/issues/detail?id=360388](https://code.google.com/p/chromium/issues/detail?id=360388) dated 20140431 the status is fixed!

---

