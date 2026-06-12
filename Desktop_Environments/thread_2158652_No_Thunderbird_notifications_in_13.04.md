---
title: "No Thunderbird notifications in 13.04"
date: 2013-06-29
forum: Desktop Environments
---

### Post by thebelial on 2013-06-29
After reinstalling Xubuntu 13.04 I noticed there's no "new mail" notifications showing up when receiving new messages. Was wondering if I'm missing something or if this a new bug? Last time Xubuntu was installed, everything was stock and it worked. Haven't done anything different this time.

---

### Post by LewisTM on 2013-06-30
Since 12.10, Xubuntu doesn't support the messaging indicator (indicator-messages), which is in charge of showing new mail and other notifications in Ubuntu. The reason is that it is written for GTK3 and Xfce is still using GTK2. 
The workaround is to install the Firetray addon in Thunderbird, which looks and acts very much like the old indicator.

Cheers!

---

