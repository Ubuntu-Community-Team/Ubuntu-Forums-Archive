---
title: "Overlay Scrollbars missing on some Unity/Gnome applications after installing KDE"
date: 2012-10-23
forum: Desktop Environments
---

### Post by enemotrop on 2012-10-23
Hello,

I use Ubuntu 12.04 LTS with the default desktop environment (Unity 3D), the default Ambiance theme, and always found the overlay scrollbars (Ayatana) very nice.

A few days ago, I installed KDE, and, after that, I've noticed that some gtk native apps, as gnome-terminal or gedit, have lost the overlay scrollbars, displaying now the classic ones.

I've tried to solve the problem with MyUnity, Unsettings and Ubuntu-Tweak, with no effect (in fact, the overlay scrollbars are detected as 'on' by these programs, and are installed and working, because in SOME apps and dialogues they still on). The problem is with the main part of the native gtk apps that are included in the default Ubuntu installation, that are supposed to support the Ayatana scrollbars without trouble in Precise and, in my case, have disappeared after KDE joined the party.

Any ideas to restore them?

I'm using the 32 bit version of Ubuntu 12.04 LTS, with Gnome 3.4.2, kernel 3.2.0-32-generic-pae and Unity 5.16.

Thank you.

---

### Post by diesch on 2012-11-01
What output do you get if you run

```
echo $UBUNTU_MENUPROXY
```

on in a Terminal?

---

