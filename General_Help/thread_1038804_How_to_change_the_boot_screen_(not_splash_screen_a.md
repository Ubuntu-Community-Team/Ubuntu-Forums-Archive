---
title: "How to change the boot screen (not splash screen after login) in 8.04 ?? help needed"
date: 2009-01-13
forum: General Help
---

### Post by neodare on 2009-01-13
How to change the boot screen (not splash screen after login) in 8.04 ?? im a new bee in ubuntu ......

---

### Post by hivelocitydd on 2009-01-13
If you are trying to change the login screen (GDM):
Open System --> Administration --> Login Window

If you are trying to change the login splash screen, you'll need to open terminal and type:

sudo apt-get install gnome-splashscreen-manager

Open: System --> Preferences --> Splash Screen
Choose the Splash Screen you want to use and click activate.
You can download splash screens at gnome-look.org

---

### Post by neodare on 2009-01-14
i want to change that first ubuntu loading screen with ubuntu logo(that comes before login window)...not the splash or login screen......

---

### Post by blackened on 2009-01-14
> **neodare said:**
> i want to change that first ubuntu loading screen with ubuntu logo(that comes before login window)...not the splash or login screen......

It's called the usplash screen. You can change it by downloading a new theme, installing startup manager, change to the theme you downloaded using startup manager.

Usplash themes can be found by using the search function (search for, duh, usplash) at [http://gnome-look.org]("http://gnome-look.org")

Startup Manager can be installed via apt-get, aptitude, or Synaptic:

```
sudo apt-get install startupmanager
```

---

### Post by neodare on 2009-01-16
> **blackened said:**
> It's called the usplash screen. You can change it by downloading a new theme, installing startup manager, change to the theme you downloaded using startup manager.

Usplash themes can be found by using the search function (search for, duh, usplash) at [http://gnome-look.org]("http://gnome-look.org")

Startup Manager can be installed via apt-get, aptitude, or Synaptic:

```
sudo apt-get install startupmanager
```



thanks ..... but i dnt have internet in home ...can i manually download it from some where and insatll it at home ???

---

### Post by blackened on 2009-01-16
> **neodare said:**
> thanks ..... but i dnt have internet in home ...can i manually download it from some where and insatll it at home ???

[http://sourceforge.net/project/showfiles.php?group_id=206283&package_id=246755]("http://sourceforge.net/project/showfiles.php?group_id=206283&package_id=246755")

To avoid running into unresolvable dependency problems I would suggest downloading version 1.9.11-1_all.deb as that is what appears to be in the 8.10 repositories.

---

