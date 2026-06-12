---
title: "No tray in tint2 when starting OpenBox session"
date: 2012-05-26
forum: Desktop Environments
---

### Post by slavssn on 2012-05-26
Hi,

After logging in using OpenBox session, my tint2 starts immediately, because I put it in autostart file. However, there's no tray even though I know it's set in tint2rc file. If I kill the program and then launch it again, the notification area is visible. I'm not sure whether it's related to tint2 or OpenBox, but maybe somebody could help me here.

Regards,
slavssn

---

### Post by Rodney9 on 2012-05-26
Tint2 tutorial might help you - 

[https://code.google.com/p/tint2/wiki/Configure](https://code.google.com/p/tint2/wiki/Configure)

[http://crunchbanglinux.org/forums/topic/16997/how-to-latest-tint2-code-and-new-tint2-additions/](http://crunchbanglinux.org/forums/topic/16997/how-to-latest-tint2-code-and-new-tint2-additions/)


Rodney

---

### Post by slavssn on 2012-05-27
Thank you. I'm obviously aware of that tutorial and I find configuring the panel rather easy. There's no answer to my problem though, neither is in VastOne's tutorial (superbly written, has to be said). Now I've got a fresh and up-to-date tint2 and still have to kill it and then start again in order to see the tray.

**Edit:** Thank God (well, thank corenominal) there's CrunchBang Linux! I was stupid enough to put just```
#this is my autostart file
tint
```in autostart, where I should've put```
#this is my autostart file
tint &
```instead, as I found out by reading default CB autostart file.

---

