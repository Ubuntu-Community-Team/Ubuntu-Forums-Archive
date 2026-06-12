---
title: "Xubuntu shortcuts not working"
date: 2020-06-27
forum: Desktop Environments
---

### Post by ricardo-pedri on 2020-06-27
None of the shortcuts in the shortcut's menu work. The keyboard is working normally.
What could be causing this?

---

### Post by guiverc on 2020-06-27
You haven't said what release you are using, however I'd try

```
xfsettingsd --replace &
```

Is this an installed or 'live' system?

---

### Post by ricardo-pedri on 2020-06-28
Thank you, I tried this code and got:


```

$ (xfsettingsd:2319): xfsettingsd-CRITICAL **: 12:12:39.758: Stored Xfconf properties disable all outputs, aborting.

```

I'm running an installed system.

XFCE 4.12
on

```

$ uname -a
Linux 5.3.0-59-generic #53~18.04.1-Ubuntu SMP Thu Jun 4 14:58:26 UTC 2020 x86_64 x86_64 x86_64 GNU/Linux

```

---

