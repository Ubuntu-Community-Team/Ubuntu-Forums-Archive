---
title: "Safe to remove these unnecessary apps?"
date: 2006-08-11
forum: Desktop Environments
---

### Post by okok on 2006-08-11
While marking applications I do not need for removal in synaptic, some produced warnings that removing this or that item (say abiword) would remove packages like xubuntu-desktop. Does this mean that the removal of such applications will cause the removal of xfce, in this case, or just the removal of a meta-package, but leave actual components in place? And if I am correct, what difference does it make if I remove meta-packages if I know which applications I want and don't want?

---

### Post by Ramses de Norre on 2006-08-11
It does not matter when you remove xubuntu-desktop it's just a meta package like you said, which means a package with a hell of a lot useful dependencies but no contents itself. As soon as you remove one of the dependencies the meta package gets removed too, but all the other apps it installed, will stay installed. No worries thus ;)

---

### Post by mssever on 2006-08-11
The only concern in removing meta-packages is that if something gets ADDED (as a dependency), you won't get it automatically, and you might not even know that it's available.

---

### Post by okok on 2006-08-11
Thanks. But doesn't each of the component packages in such meta-packages come with their own dependencies, so that when I install or updgrade one of them, the others are updated as well?

---

### Post by Ramses de Norre on 2006-08-11
He means if they add a package to ubuntu-desktop for example, that package would be automaticaly installed when ubuntu-dekstop is installed.

---

### Post by okok on 2006-08-12
Thank you for your explanations.

---

