---
title: "How to Disable Compiz???"
date: 2007-10-14
forum: Desktop Effects &amp; Customization
---

### Post by wadpro on 2007-10-14
I have managed to run Compiz Fusion with ATI Xpress 1150 graphic card but i dont know how to disable it?

Kubuntu crashed after using these commands:

```
killall compiz.real
killall compiz
metacity --replace --display :0 &
```

How can I fix my system?

---

### Post by michael37 on 2007-10-17
> **wadpro said:**
> I have managed to run Compiz Fusion with ATI Xpress 1150 graphic card but i dont know how to disable it?

Kubuntu crashed after using these commands:

```
killall compiz.real
killall compiz
metacity --replace --display :0 &
```

How can I fix my system?

How about uninstalling compiz?  Kubuntu should fall back to using metacity.

sudo apt-get remove --purge compiz*

---

### Post by Forlong on 2007-10-17
> **wadpro said:**
> I have managed to run Compiz Fusion with ATI Xpress 1150 graphic card but i dont know how to disable it?
```
kwin --replace
```

---

