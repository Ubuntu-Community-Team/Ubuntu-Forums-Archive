---
title: "How much of a difference between Kubuntu and Ubuntu?"
date: 2005-09-07
forum: Desktop Environments
---

### Post by adwait on 2005-09-07
Hello!

Well, I used KDE for the first time, and like a lot better than GNOME. I also set my default Desktop Manger to be kdm, so does that mean I am Kubuntu? Or is there more of a difference between the two distros? Also, their release schedules are very different, so whn I up grade to breezey, will the KDE components be upgraded or not?

---

### Post by djib on 2005-09-07
[QUOTE=adwait]Hello!

Well, I used KDE for the first time, and like a lot better than GNOME. I also set my default Desktop Manger to be kdm, so does that mean I am Kubuntu? Or is there more of a difference between the two distros? Also, their release schedules are very different, so whn I up grade to breezey, will the KDE components be upgraded or not?[/QUOTE]
 Hello

If you do :
```
sudo apt-get install kubuntu-desktop
sudo apt-get remove --purge ubuntu-desktop
```
you will get a kubuntu.

Later, when you upgrade your system, you will stay kubuntu for as long as you don't remove the kubuntu desktop...

---

### Post by adwait on 2005-09-07
I don't won't to entirely remove GNOME, because my father and brother use gnome, I like to experiment with different things :)

---

### Post by djib on 2005-09-07
[QUOTE=adwait]I don't won't to entirely remove GNOME, because my father and brother use gnome, I like to experiment with different things :)[/QUOTE]
 Well, then you just install kubuntu-desktop without removing ubuntu-desktop. When you do an upgrade or dist-upgrade, both will be upgraded (provinding they have changed).

---

### Post by snowjunkie on 2005-09-07
If you keep both, how do you alternate between the both of them?  Also, what size of disk space does the kubuntu-desktop install take up?

Thanks!

---

### Post by adwait on 2005-09-07
Kubuntu desktop takes about 66MB of archives and takes 192 MB of extra space. You can alternate between them from the sessions menu at the login screen, just select KDE instead of GNOME. You have the option of using Gnome Desktop Manger (GDM) or K Desktop Manager (KDM). GDM is what Ubuntu uses by default. It doesn't matter which one you use, you can start either by using any of the desktop managers.

---

### Post by djib on 2005-09-07
[QUOTE=adwait]It doesn't matter which one you use, you can start either by using any of the desktop managers.[/QUOTE]

That's right, but if you use kdm you won't be able to reboot from Gnome (you will have to shutdown X, then reboot) and same in kde if you use gdm.

---

### Post by snowjunkie on 2005-09-11
I've installed kde using the apt-get install kubuntu-desktop.  It's working great.  During the installation I switched to kdm as the default window manager.

I tried to remove gnome using the --purge ubuntu-desktop I seen in another thread.  However, when booting up it still notes that it is not starting the gnome window manager.

How do I remove gnome entirely?

Alastair.

---

### Post by adwait on 2005-09-11
That's because gdm is in rcS.d. Run
```
sudo rcconf 
```

And uncheck gdm.

---

