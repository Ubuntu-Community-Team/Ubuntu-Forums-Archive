---
title: "Can't find an option to shutdown"
date: 2011-03-03
forum: Desktop Environments
---

### Post by robro on 2011-03-03
Hi everyone :),
I am running kde 4.5.1 and when I go to kmenu>leave, I see everything but an option to shut down :|,

Thanks for your help.

---

### Post by def_init_ on 2011-03-03
Can you just add a "shutdown -h now kthxbye" script to the menu?

---

### Post by ankspo71 on 2011-03-03
Hi,
If you installed the KDE (or Kubuntu) desktop environment on top of Ubuntu, then this problem might be happening because you are still using GDM as your display manager. GDM isn't as compatible as KDM is for the KDE desktop. Users that want to continue using GDM will have to log out first then shutdown from the options in the login window.

Or you can switch display managers by using the following command:
```
sudo dpkg-reconfigure gdm
```
Switching from GDM to KDM should give you the shutdown option back in the KDE start menu (after the next restart).

Hope this helps.

---

### Post by robro on 2011-03-03
> **ankspo71 said:**
> Hi,
If you installed the KDE (or Kubuntu) desktop environment on top of Ubuntu, then this problem might be happening because you are still using GDM as your display manager. GDM isn't as compatible as KDM is for the KDE desktop. Users that want to continue using GDM will have to log out first then shutdown from the options in the login window.

Or you can switch display managers by using the following command:
```
sudo dpkg-reconfigure gdm
```
Switching from GDM to KDM should give you the shutdown option back in the KDE start menu (after the next restart).

Hope this helps.

Thank you, that worked great :) although I don't really like the kdm login screen :|
is there any way to be able to have the gnome login screen, and be able to shutdown from the kmenu?

If there isn't I could live with it I guess :-?

ps. I have both ubuntu and kubuntu installed, I just choose whichever at the login screen.

---

### Post by ankspo71 on 2011-03-03
Hi,
The KDM theme can be customized at System Settings > Login Screen, but I don't think it is possible to use Ubuntu's own GDM theme. 

KDE-Look.org has many KDM4 themes to choose from though.
[http://kde-look.org/index.php?xcontentmode=41](http://kde-look.org/index.php?xcontentmode=41)

Themes can be downloaded and installed through System Settings > Login Screen > "theme" (tab).

Hope this helps.

---

### Post by robro on 2011-03-03
I'm looking through them right now and they look great I think I can find one I like :)

Thank you :)

---

