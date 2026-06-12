---
title: "indicator-applet and empathy"
date: 2009-10-31
forum: Desktop Environments
---

### Post by zubaran on 2009-10-31
Is there a way to remove empathy or anything from indicator-applet list? I still use pidgin and this empathy entry annoys me, besides I can activate it by mistake.

---

### Post by Bruce H on 2009-10-31
sudo apt-get remove empathy

If you are happy with Pidgin, there's no reason to use Empathy. However, GTalk voice works in Empathy, but (as far as I know) not in Pidgin.

---

### Post by zubaran on 2009-11-01
That is not solution. Of course it would work for me since I am the only one that uses my computer, but if you assume that I have many users that is not the case.

---

### Post by ukblacknight on 2009-11-06
```
sudo rm /usr/share/indicators/messages/applications/empathy
```

This would remove it for ALL users though.

---

