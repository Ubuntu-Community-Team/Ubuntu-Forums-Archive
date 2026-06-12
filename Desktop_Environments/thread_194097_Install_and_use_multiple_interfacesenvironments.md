---
title: "Install and use multiple interfaces/environments?"
date: 2006-06-10
forum: Desktop Environments
---

### Post by hxx4 on 2006-06-10
I'm interested in trying out KDE and XFCE in ubuntu, but I want it all in one installation. So how can I add KDE and XFCE to ubuntu, and will it be easy to switch between them?

---

### Post by adwait on 2006-06-10
Just use
```
sudo apt-get install kubutu-desktop
sudo apt-get install xubuntu-desktop
```

This will download and install KDE and XFXE respectively. After that, at the login screen, click on Menu and you can selec the environment.

---

### Post by aysiu on 2006-06-11
"Trying out" to me indicates that you might consider removing them later, in which case you'll want to use *aptitude* instead of *apt-get*.

```
sudo aptitude update
sudo aptitude install kubuntu-desktop
sudo aptitude install xubuntu-desktop
```

---

