---
title: "Input signal out of range"
date: 2007-11-02
forum: Desktop Environments
---

### Post by luciantodoran on 2007-11-02
When I enter and leave Ubuntu I see an unclear double-image desktop with that filling bar and with the message: ”Input signal out of range”. I have installed Ubuntu twice and I get the same message. What can I do to solve this problem?

---

### Post by markusf21 on 2007-11-02
Try this:
```
gksu gedit /etc/usplash.conf 
```
and make sure it's not trying to use a resolution you monitor can't handle

---

