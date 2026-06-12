---
title: "KPersonalizer"
date: 2006-09-24
forum: Desktop Environments
---

### Post by AquaFox90 on 2006-09-24
It just keeps starting automatically with KDE. Everytime I login it starts THEN the Desktop Enviroment loads.. What the hell?

Please help.

---

### Post by Jucato on 2006-09-24
Press Alt+F2 then type in this command:

```
kdesu kate /usr/bin/startkde
```
(Start kate with Administartor privileges and open the file/script startkde in /usr/bin/)

Look for this line:

> kpersonalizerrc General FirstLogin true

And change "true" to "false". Save it, and you won't be bothered by KPersonalizer any longer.

---

### Post by AquaFox90 on 2006-09-24
Thanks mate.

---

