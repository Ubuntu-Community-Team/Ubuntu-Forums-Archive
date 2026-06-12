---
title: "Restore screen brightness/gamma after playing a game"
date: 2006-09-27
forum: Gaming &amp; Leisure
---

### Post by izmaelis on 2006-09-27
I managed to run my favourite Lineage 2 Chronicles 5 on Ubuntu box. The game starts and works fine, but screen is too bright after exiting it. It looks like wine adjusts gamma/brightness and doesn't restore it in the end. Is there any way to restore brightness settings manualy or is my wine missconfiged somewhere?

---

### Post by DoktorSeven on 2006-09-27
Open a console and type **xgamma -gamma 1.0**

---

### Post by izmaelis on 2006-09-28
> **DoktorSeven said:**
> Open a console and type **xgamma -gamma 1.0**

Thank you. It does the trick.

---

