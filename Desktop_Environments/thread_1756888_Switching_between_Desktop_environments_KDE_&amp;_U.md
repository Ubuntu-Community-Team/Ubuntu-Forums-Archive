---
title: "Switching between Desktop environments KDE &amp; Unity."
date: 2011-05-12
forum: Desktop Environments
---

### Post by GreatKeyHunter on 2011-05-12
Hi, currently i run both KDE and Ubuntu Unity 11.04 on my machine.  I have encountered a little problem when switching desktop environments.  With KDE, i prefer to use KWin as my windows manager (since i find it highly polished), and with Unity, compiz (not by choice).  The problem is that if i don't switch the windows manager to compiz before switching over to unity, all hell breaks loose.  Same with switching over from Unity to KDE. 

The only solution i have found is to switch to Classic Ubuntu. and use the compiz fusion icon to select the windows manager in order to avoid any problems.  

My question is, when i log onto the either KDE or Unity, how can i load the correct desktop environment in case it crashes (which it has)?

Note: this has also become a concern to me because of 11.10 removing the classic gnome.  If the proper window manger can be loaded before entering the preferred desktop environment KDE, Gnome3 or Unity, this would be awesome.

---

### Post by Krytarik on 2011-05-12
It seems like the set window manager of either session option crashes for some reason upon login, like yourself assume. And it is curious that the interim login to classic Gnome fixes that for either session option.

However, to work around that issue you could put launchers on the desktops of either DE for the commands to re-/load either respective WM.

Compiz:
```
compiz --replace
```KWin:
```
kwin --replace
```Greetings.

---

