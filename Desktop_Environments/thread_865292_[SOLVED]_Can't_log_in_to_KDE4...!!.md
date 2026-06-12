---
title: "[SOLVED] Can't log in to KDE4...???!!"
date: 2008-07-20
forum: Desktop Environments
---

### Post by armageddon08 on 2008-07-20
I just installed KDE4 from this repository:
deb [http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu](http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu) hardy main
But now I cannot log into KDE4. I am using entrance as my login manager.
Whenever I select KDE4 as the session and then enter my username and password, the screen blacks out and after a few seconds I come back to entrance!!

Anybody can tell me why??? Please seriously need some help!!

---

### Post by armageddon08 on 2008-07-20
C'mon guys I need some help!!!

---

### Post by benerivo on 2008-07-20
Have you ever been able to log in to kde4? The launchpad repositories should be fine, it may just be that there is some unresolved bug, as they are really only for beta realeases. Having said that, the current status of kde4 in launchpad is the release candidate of 4.1.

If you have been able to log in to kde4 previously, then rename your /home/armageddon08/.kde4 folder to .kde4BACKUP. This will effectively remove your kde4 settings and when you log in it will be like the first time you ever did.

Also try using this code to identify any xserver crash...```
cat .xsession-errors
```

---

### Post by armageddon08 on 2008-07-20
Actually I installed Kde for the first time on my comp........I was using Gnome before. I can log into Gnome and Enlightenment also but not into KDE4.

---

### Post by armageddon08 on 2008-07-20
Never mind solved the previous problem myself.

But now I want to stop GNOME startup-items from starting in KDE. Anybody could tell me how to do this?

---

### Post by YoutubesUbunuLee on 2008-07-21
> **armageddon08 said:**
> Never mind solved the previous problem myself.

But now I want to stop GNOME startup-items from starting in KDE. Anybody could tell me how to do this?

Sorry to say this man but its better to just dual boot Kubuntu and Ubuntu if you want both worlds. Mixed up applications and start up applications can be changed but whatever you do in one effects the other.

---

### Post by armageddon08 on 2008-07-21
okay...........thanks!

---

### Post by Quasaur on 2008-08-04
armageddon08,

Could you be so kind as to tell us how you solved the problem?

I had kde3 & kde4 running fine before i install e17/entrance.

For some reason kde4 wont start from Entrance...probably some simple config thing...?

> **armageddon08 said:**
> Never mind solved the previous problem myself.

But now I want to stop GNOME startup-items from starting in KDE. Anybody could tell me how to do this?

---

### Post by armageddon08 on 2008-08-06
> **Quasaur said:**
> armageddon08,

Could you be so kind as to tell us how you solved the problem?

I had kde3 & kde4 running fine before i install e17/entrance.

For some reason kde4 wont start from Entrance...probably some simple config thing...?

Yup......I just stopped using Entrance as my login manager..probably it is a bit buggy at the moment. Use GDM or KDM as your default login manager. Set it up as follows:
```
sudo dpkg-reconfigure kdm-kde4
``` or 
```
sudo dpkg-reconfigure gdm
```
It will then ask you to choose your default login manager. Choose kdm-kde4 or if you have gnome choose gdm.

I hope:) this will solve your problem.

---

