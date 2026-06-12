---
title: "After installing Skype, KDE effects are gone"
date: 2012-01-04
forum: Desktop Environments
---

### Post by spielball on 2012-01-04
First, I was really pleased by Kubuntu. I thought it's a good alternative to Unity. But right after the installation, already so many problems and crashes came up. It's awful. For instance, I only installed Skype on a fresh install of Kubuntu 11.10. After that, all desktop effects are gone. No 'illuminated' or transparent windows anymore. Is there a fix?

---

### Post by spielball on 2012-01-06
Solved. The Skype installer, for some reason, removes packages of plasma-desktop. Somewhere I read it has to do with Skype being a 32-bit appliation. Weird. Anyway, I had to re-install plasma-desktop:

```
sudo apt-get update && sudo apt-get install --reinstall plasma-desktop
```After that, I had to re-enable desktop effects. Now everything works fine. And KDE with icon-tasks app rocks :D

---

### Post by tkabir11 on 2012-01-06
> **spielball said:**
> Solved. The Skype installer, for some reason, removes packages of plasma-desktop. Somewhere I read it has to do with Skype being a 32-bit appliation. Weird. Anyway, I had to re-install plasma-desktop:

```
sudo apt-get update && sudo apt-get install --reinstall plasma-desktop
```After that, I had to re-enable desktop effects. Now everything works fine. And KDE with icon-tasks app rocks :D

Looks like I might have to watch out for the same problem when I install skype on my KDE desktop.

---

### Post by nfunqn on 2012-07-11
> **tkabir11 said:**
> Looks like I might have to watch out for the same problem when I install skype on my KDE desktop.

What was your experience?  Did you get the same problem?

---

