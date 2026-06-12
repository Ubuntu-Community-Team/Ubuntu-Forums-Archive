---
title: "Switching from unity to kde, login screen problem"
date: 2013-11-18
forum: Desktop Environments
---

### Post by jefft255 on 2013-11-18
I switched from ubuntu to kubuntu today using apt-get install  kubuntu-desktop, which worked fine except from the fact that the login  screen that pops up when I boot up my computer is still the unity login  screen. Is there any way I can change it? I've been looking for a few  hours now and I have no clue... (I'm using 13.10)

---

### Post by ajgreeny on 2013-11-18
I don't know which display manager is used by kubuntu but assuming it's kdm you need to run command ```
sudo dpkg-reconfigure kdm
```and choose kdm from the options shown.

You may also find that installing **lightdm-kde-greeter** is needed to theme lightdm to your taste without bothering about kdm, but it is so long since I used kde that I have no idea what these things look like now.

---

### Post by drmrgd on 2013-11-18
By chance, have you tried changing the theme in System Settings->Login Screen?  That's usually where I go to change my login screen.

---

### Post by public3 on 2013-11-19
I would recommend using light-dm with KDE, instead of KDM.

---

### Post by buzzingrobot on 2013-11-20
When you install a display manager, you are typically asked during its installation if you want to use it or the currently installed DM.  Perhaps "Kubuntu-Desktop" does not include a new DM.

---

