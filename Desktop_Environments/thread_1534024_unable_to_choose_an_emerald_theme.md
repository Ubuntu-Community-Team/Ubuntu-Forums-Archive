---
title: "unable to choose an emerald theme"
date: 2010-07-18
forum: Desktop Environments
---

### Post by gagx on 2010-07-18
so i cant choose an emerald theme, nothing happens when i try. what do i do? thanks in advance

---

### Post by TheWeakSleep on 2010-07-19
are you using it as your window decorator? try getting compiz fusion icon to easily switch window decorators. you can find it in the software center or through synaptic

---

### Post by howefield on 2010-07-19
After selecting the emerald theme, press Alt + F2 keys and type

```
emerald --replace
``` 

in the run box, then press the run button.

To make it start when you reboot, open System > Preferences > CompizConfig Settings Manager and click on Window Decoration button, then in the command field type emerald --replace.

(You have to have compizconfig-settings-manager installed first, which can be done through Synaptic Package Manager)

---

### Post by gagx on 2010-07-19
> **howefield said:**
> After selecting the emerald theme, press Alt + F2 keys and type

```
emerald --replace
```in the run box, then press the run button.

To make it start when you reboot, open System > Preferences > CompizConfig Settings Manager and click on Window Decoration button, then in the command field type emerald --replace.

(You have to have compizconfig-settings-manager installed first, which can be done through Synaptic Package Manager)


thanks, worked like a charm

---

