---
title: "Compiz Disables itself after reboot"
date: 2009-04-16
forum: Desktop Environments
---

### Post by Lorenzo1985 on 2009-04-16
Compiz Disables itself after reboot

After an upgrade to Jaunty I have Window manager issues.
Every time I reboot, when I come back, Visual affects are disabled. I can enable them by going to System >Preferences>Appearance>Visual affects>Normal
 but this setting never sticks. 

Compiz works fine when it's running

Any guesses what the next steps are, or pointers as to what info you need to help me diagnose the problem?

---

### Post by JECHO on 2009-04-16
> **Lorenzo1985 said:**
> Compiz Disables itself after reboot

After an upgrade to Jaunty I have Window manager issues.
Every time I reboot, when I come back, Visual affects are disabled. I can enable them by going to System >Preferences>Appearance>Visual affects>Normal
 but this setting never sticks. 

Compiz works fine when it's running

Any guesses what the next steps are, or pointers as to what info you need to help me diagnose the problem?


Add:
```
compiz --replace
```

to your startup programs list and it should be fixed.

---

