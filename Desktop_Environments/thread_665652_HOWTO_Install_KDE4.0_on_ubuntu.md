---
title: "HOWTO: Install KDE4.0 on ubuntu"
date: 2008-01-12
forum: Desktop Environments
---

### Post by zubat on 2008-01-12
Step1.
Open terminal and type 
```
sudo gedit /etc/apt/sources.list
```

Step2:
Add this to the file:

```
deb http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu gutsy main
```

Save changes to the file on close it.

Step3.
Type: 
sudo aptitude update && sudo aptitude install kde4


Step4.
Once this has finiched log out then change session to KDE 4 then log in, If you experiance slow performance in KDE reboot your machine and change session to KDE again.

If I have made a mistake correct me thanks.

---

### Post by K.Mandla on 2008-01-13
Moved to Desktop Environments.

---

### Post by psychicdragon on 2008-01-13
1 small correction: you want to install the kde4 package; not kde. It's also worth noting that you can install kde4-core instead if you just want to try it out without installing literally every KDE application.

---

### Post by teishu on 2008-01-13
thanks for this i'll give it a try later...

---

### Post by bruceli on 2008-01-13
> **psychicdragon said:**
> 1 small correction: you want to install the kde4 package; not kde. It's also worth noting that you can install kde4-core instead if you just want to try it out without installing literally every KDE application.

Do I need to remove the KDE 3 first? And how? Thanks.

---

### Post by psychicdragon on 2008-01-13
> **bruceli said:**
> Do I need to remove the KDE 3 first? And how? Thanks.
KDE 4 can be installed alongside KDE 3.5 without any problems.

---

