---
title: "Installing a new keyboard"
date: 2022-08-15
forum: Desktop Environments
---

### Post by nibal on 2022-08-15
Hi

I have a freshly installed Kubuntu 20.04.
Added a new language from regional settings, and need to add a new keyboard for it.
In ubuntu the option to add a new keyboard is on the same page with the new language.
Not in Kubuntu. Where is it?

TIA
Nikos

---

### Post by #&amp;thj^% on 2022-08-15
Keyboard layout is in the below

KDE System settings > **Input Devices > Keyboard > Layouts**
or from knosole:
```
kcmshell5 kcm_keyboard
```

---

### Post by nibal on 2022-08-15
> **1fallen said:**
> Keyboard layout is in the below

KDE System settings > **Input Devices > Keyboard > Layouts**
or from knosole:
```
kcmshell5 kcm_keyboard
```

Thank you so much,

It is actually just "System Settings -> Input Devices -> Layouts" (Not KDE)

Now it's working fine:)

---

