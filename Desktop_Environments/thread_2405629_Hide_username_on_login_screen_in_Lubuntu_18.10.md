---
title: "Hide username on login screen in Lubuntu 18.10"
date: 2018-11-08
forum: Desktop Environments
---

### Post by Charlotte18 on 2018-11-08
Does anyone know how to hide the username on the login screen in the new Lxqt version of lubuntu 18.10? It doesn't seem to me that 18.10 is using lightdm anymore.

---

### Post by deadflowr on 2018-11-09
Lubuntu 18.10 now uses sddm.
To set it with to not show usernames you need to set a theme which doesn't list usernamse:
see:
[https://ubuntuforums.org/showthread.php?t=2402711]("https://ubuntuforums.org/showthread.php?t=2402711")

On top of that you'll most likely need to edit the sddm.conf file in /etc/sddm.conf
and change the theme to whichever theme you choose.
ArchLinux wiki is a good starting point for getting it together and understanding how and what needs to be done:
[https://wiki.archlinux.org/index.php/SDDM]("https://wiki.archlinux.org/index.php/SDDM")

---

### Post by Charlotte18 on 2018-11-09
Maybe I didn't try hard enough, but I could not find any such ssdm themes in the Ubutnu repositories. I did find that installing lightdm in Lubuntu 18.10 allowed me to go back to that dm, which I am already familiar with, and then hide the username at the login screen.

---

