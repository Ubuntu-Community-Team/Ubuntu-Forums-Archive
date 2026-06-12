---
title: "[SOLVED] taking setting back on ubuntu to the fist time"
date: 2008-12-30
forum: General Help
---

### Post by zerre on 2008-12-30
hi every one. I have a problem about compiz. I have changed some setting on compiz and everything confused.even I cant clik left and rigt on the mouse . I need to learn how to take all changing on compiz to the back.

---

### Post by gettinoriginal on 2008-12-30
This will reset compiz to default, in terminal:
```
gconftool-2 --recursive-unset -a /apps/compiz
```

---

### Post by uidb4056 on 2008-12-30
> **zerre said:**
> hi every one. I have a problem about compiz. I have changed some setting on compiz and everything confused.even I cant clik left and rigt on the mouse . I need to learn how to take all changing on compiz to the back.

This link [http://forlong.blogage.de/entries/2008/4/26/How-to-set-up-Compiz-Fusion-074](http://forlong.blogage.de/entries/2008/4/26/How-to-set-up-Compiz-Fusion-074) could help you to set-up Compiz right.

---

### Post by zerre on 2009-01-02
> **gettinoriginal said:**
> This will reset compiz to default, in terminal:
```
gconftool-2 --recursive-unset -a /apps/compiz
```
tahnks for helping. &#305;t solved my problem.

---

### Post by steveneddy on 2009-01-03
Please mark this as solved then.

Thanks.

---

