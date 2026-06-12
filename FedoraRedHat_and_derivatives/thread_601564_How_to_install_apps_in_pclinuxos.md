---
title: "How to install apps in pclinuxos"
date: 2007-11-03
forum: Fedora/RedHat and derivatives
---

### Post by Istonian on 2007-11-03
I have used ubuntu all my linux life, so I tried pclinuxos. I can't find out how to install stuff on pclinuxos. Synaptic does not have my programs I need. How do I install RMP packages. I downloaded a RPM file and can't get it to run. I am confused.

---

### Post by mrvertigo on 2007-11-03
mmmmmmmmm odd

---

### Post by mindtrick on 2007-11-03
Did you reload Synaptic? Or try another mirror?

---

### Post by igknighted on 2007-11-04
```
cd /path/to/package
rpm -ivh packagename.rpm
```

---

### Post by SunnyRabbiera on 2007-11-09
kpackage is another good way to install non native apps.
WARNING!: do try to keep to the packages in the repo's if possible.

---

