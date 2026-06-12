---
title: "How can I install one of these KDM themes?"
date: 2008-01-01
forum: Desktop Effects &amp; Customization
---

### Post by rootware on 2008-01-01
I tried to save the file and load it from K -> System -> Login Window but it's not working, it does not appear in the themes list :(

Tell me please what can I do?

---

### Post by FuturePilot on 2008-01-01
Try this
```
sudo apt-get install kdmtheme
```
This will install a KDM Theme Manager which can be found under Kmenu>System Settings>Appearance>KDM

---

### Post by rootware on 2008-01-02
> **FuturePilot said:**
> Try this
```
sudo apt-get install kdmtheme
```
This will install a KDM Theme Manager which can be found under Kmenu>System Settings>Appearance>KDM

Call me blind FuturePilot, but I see no Administrator Mode in this menu so I can access the Theme Manager :(

[[IMG]http://img514.imageshack.us/img514/3427/noadminbuttonnc2.th.png[/IMG]](http://img514.imageshack.us/my.php?image=noadminbuttonnc2.png)

---

### Post by BillDozer on 2008-01-02
> **rootware said:**
> Call me blind FuturePilot, but I see no Administrator Mode in this menu so I can access the Theme Manager :(

Does your user have administrative rights. Correct me if I am wrong, but isn't the button only visible when you are allowed to press it?

---

### Post by rootware on 2008-01-02
> **BillDozer said:**
> Does your user have administrative rights. Correct me if I am wrong, but isn't the button only visible when you are allowed to press it?

Well it looks like not, because for example on Font Installer I have that button :confused::confused::confused:
[[IMG]http://img179.imageshack.us/img179/7259/buttonck8.th.png[/IMG]](http://img179.imageshack.us/my.php?image=buttonck8.png)

---

### Post by FuturePilot on 2008-01-02
Are you using Feisty? I remember Kubuntu Feisty had a missing Admin button in KDM theme. You would have to launch the system settings as root.

---

### Post by rootware on 2008-01-02
> **FuturePilot said:**
> Are you using Feisty? I remember Kubuntu Feisty had a missing Admin button in KDM theme. You would have to launch the system settings as root.

Yep, Feisty in here.

How can I log onto root when root is locked by default? :confused:

---

### Post by FuturePilot on 2008-01-02
You don't need to login as root. Just open a terminal and enter 
```
kdesu kcontrol
```
This will run kcontrol instead of system settings but it does the same thing. Find the KDM Theme Manager and change the theme.

---

### Post by rootware on 2008-01-02
> **FuturePilot said:**
> You don't need to login as root. Just open a terminal and enter 
```
kdesu kcontrol
```
This will run kcontrol instead of system settings but it does the same thing. Find the KDM Theme Manager and change the theme.

It worked, thanks a lot FuturePilot and good luck in your pilot carrier ;)

---

