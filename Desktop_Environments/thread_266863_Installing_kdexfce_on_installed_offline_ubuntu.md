---
title: "Installing kde/xfce on installed offline ubuntu"
date: 2006-09-27
forum: Desktop Environments
---

### Post by cetheriel on 2006-09-27
is there a way to install kde on a offline ubuntu 6.06?
also is there any way to install xfkce, so i can choos the session i want to run?

---

### Post by pay on 2006-09-28
I know you said offline but thats just about impossible as you need to get files. To install KDE type```
sudo apt-get install kubuntu-desktop
```into the terminal. To install XFCE type```
sudo apt-get install xubuntu-desktop
```into the terminal. They both make their own sessions that you can pick from the GDM

---

### Post by aysiu on 2006-09-28
It's not impossible if you have the Alternate CD for it.

```
sudo apt-cdrom add
sudo aptitude update
sudo aptitude install kubuntu-desktop
```

I repeat--you need the **Alternate CD**. The Desktop CD will not allow you to add a desktop environment.

---

### Post by pay on 2006-09-28
Yeah but you still have to download that cd. Or you can order Kubuntu from shipit but I don't think that you can order Xubuntu yet.

---

### Post by cetheriel on 2006-09-28
> **pay said:**
> Yeah but you still have to download that cd. Or you can order Kubuntu from shipit but I don't think that you can order Xubuntu yet.

i meant on a offline pc, not that i would be always offline.

---

### Post by aysiu on 2006-09-28
Someone has to have internet connection in order to post a question on these forums. It may not be on the main computer or the Ubuntu computer, but it's *somewhere*.

---

### Post by whizbaby on 2006-09-28
xfce also has an installer you can download from their site
[http://www.xfce.org/index.php?lang=en](http://www.xfce.org/index.php?lang=en)

---

