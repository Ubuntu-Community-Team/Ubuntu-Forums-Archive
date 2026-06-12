---
title: "[KDE] Automating KDE to start an application in a defined desktop"
date: 2007-09-18
forum: Desktop Environments
---

### Post by Levure on 2007-09-18
Hello,

Every times I start KDE, I have to manually launch several applications and manually move them to one of the 8 desktops.

Is there a way to automate the launch of application to a defined desktop via a script ?

Thanks in advance for any tips !

---

### Post by GeneralZod on 2007-09-18
If it's always the same set of apps, and you have them open the entire time, it might be worth enabling Session Management.

If not, look into kstart:

```

kstart --help

```

---

