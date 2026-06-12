---
title: "xft support in qt 3"
date: 2005-03-27
forum: Desktop Environments
---

### Post by candyman on 2005-03-27
I'm only just new to Ubuntu and it seems like libqt3 installs by default without xft support.  I select from ttf fonts and they look pretty jagged and ugly.  I've got both libxft1 and libxft2 installed.  Any help appreciated.

---

### Post by stilus on 2005-03-27
I'm not sure, but I think your ~/.qt/qtrc should have 
```

enableXft=true
useXft=true

```
 in it... 

Good luck!

---

### Post by candyman on 2005-03-27
Had that in my qtrc file but upon running qtconfig this morning my fonts are all, good like. Wierd

Thanks anyway.

---

### Post by mephisto on 2005-05-05
I had some sort of similar problem, then irealised I hadn't clicked file -> save in qtconfig :P

thats not *totally* stupid of me though at qtconfig itself remembered my settings in its own dialog but obviously didnt commit them to qt's config file until i saved. Caused me many a day of enjoyment that did - hohoho!

---

