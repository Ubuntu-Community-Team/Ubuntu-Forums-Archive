---
title: "Dell Insprion 1545 Wifi card not working?"
date: 2012-06-15
forum: Dell Ubuntu Support (CLOSED)
---

### Post by mike551345 on 2012-06-15
So i just converted my laptop to Ubuntu. i had no problems with my desktop connecting with a third party WiFi dongal. but when i tried to connect with my dell insprion 1545 it didn't see the card. need help for getting it going.

---

### Post by mikewhatever on 2012-06-15
We'll need some wireless hardware related info from you. Can you post the outputs of the following:

```
lspci -nnk | grep -iA2 net

ifconfig

rfkill list all
```

PS: Most likely, you just need to connect a cable and install the driver.

---

