---
title: "KDE took over my Splash/Login and did something to my keyring?"
date: 2012-08-07
forum: Desktop Environments
---

### Post by Minipalmer on 2012-08-07
Hey all,

I installed kubuntu-desktop on a separate user profile just to see what new extras KDE has cooked up over the last couple years. I played with it for a little while, then deleted the profile and removed kubuntu-desktop.

KDE altered my splash screen, my login screen, and now forces me to enter my password for my key ring on every login (which it didn't used to do). I've seen some answers and solutions for fixing these problems, but I don't want to have to install super-boot-manager or any other third party program to manage my splash. If it can be put on, it can be taken off :)

Thanks for your help!

Edit: Okay, changed the Splash with this command:

```
sudo apt-get remove plymouth-theme-kubuntu*
```

Edit x2: This fixed the login:

```
http://askubuntu.com/questions/138561/reset-to-default-unity-login
```

This appears to have fixed the keyring:

[http://askubuntu.com/questions/134292/unlock-login-keyring-problem-ubuntu-12-04-lts](http://askubuntu.com/questions/134292/unlock-login-keyring-problem-ubuntu-12-04-lts)

---

