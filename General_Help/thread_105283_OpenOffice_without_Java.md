---
title: "OpenOffice without Java?"
date: 2005-12-18
forum: General Help
---

### Post by liverpoolfc on 2005-12-18
I'd like to install OpenOffice, but without the version of Java in the repository that it depends on.  I'm doing development work, and I really need to use a Sun version, but the other version gets installed into /usr/bin which causes problems because it's in my PATH.

Is there a way to either install OOo without the Java dependency, or remove that version of Java afterwards without removing OOo?

---

### Post by codejunkie on 2005-12-18
[QUOTE=liverpoolfc]I'd like to install OpenOffice, but without the version of Java in the repository that it depends on.  I'm doing development work, and I really need to use a Sun version, but the other version gets installed into /usr/bin which causes problems because it's in my PATH.

Is there a way to either install OOo without the Java dependency, or remove that version of Java afterwards without removing OOo?[/QUOTE]
try running this after you install sun java 
```
sudo update-alternatives --config java
```choose the option for sun java and you should be all set hope this helps.

---

### Post by MartinG on 2005-12-18
Maybe I'm missing the point -- isn't it sufficient to select the Sun Java in OpenOffice.org's options dialog, once you've installed it?  My system finds both Sun and the gij(?) and gives me a choice.

---

### Post by liverpoolfc on 2005-12-19
I'd rather not have ANY java in my path.  Some apps and installers will use this as a default, and I'd rather set a JAVA_HOME for each app.  However, Codejunkies suggestion is better than the default.  Thanks.

---

