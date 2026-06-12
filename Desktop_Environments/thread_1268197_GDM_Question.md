---
title: "GDM Question"
date: 2009-09-16
forum: Desktop Environments
---

### Post by theiLLziLLa on 2009-09-16
Ok here is my situation, I have ubuntu 9.04 and I recently installed the KDE desktop to test it out (I will likely do a fresh install with kubuntu on the next release), anyways... After I uninstalled the KDE desktop I could not get my login to switch back to the default GDM.

Any ideas ???

---

### Post by ajgreeny on 2009-09-16
In terminal use ```
sudo dpkg-reconfigure gdm
```and choose to use gdm again instead of kdm.  You may also need to do the same with usplash, or just remove kubuntu-artwork-splash, but I'm not sure if that will have been installed with kde; however, it is if you installed kubuntu-desktop to get kde.

---

### Post by theiLLziLLa on 2009-09-17
Thank you very much, I knew it would be something easy.

---

