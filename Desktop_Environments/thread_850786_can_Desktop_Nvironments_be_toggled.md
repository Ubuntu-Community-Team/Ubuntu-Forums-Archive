---
title: "can Desktop Nvironments be toggled ??"
date: 2008-07-05
forum: Desktop Environments
---

### Post by ettercap on 2008-07-05
hello every 1

i use gnome but knw i want to change to something else...

plz tell me how to change to a differnt environment

and also very important : can these environments be TOGGLED ???:confused:

---

### Post by overdrank on 2008-07-06
> **ettercap said:**
> hello every 1

i use gnome but knw i want to change to something else...

plz tell me how to change to a differnt environment

and also very important : can these environments be TOGGLED ???:confused:

Hi and yes you can install XFCE ( example)  from synaptic manager. Then at the login window choose session and change to XFCE and login. This would apply for KDE and so on.

---

### Post by sayakb on 2008-07-06
Suppose you want to install XFCE or KDE or Fluxbox, at a terminal, do the following:
For **KDE**:
```
sudo apt-get install kubuntu-desktop
```
**KDE4**:```
sudo apt-get install kubuntu-kde4-desktop
```
**XFCE**:
```
sudo apt-get install xubuntu-desktop
```
**Fluxbox**:
```
sudo apt-get install fluxbox
```

At the login prompt (gdm), press F10 and click **Select Session** and click whichever Desktop environment or Window manager to login.

---

