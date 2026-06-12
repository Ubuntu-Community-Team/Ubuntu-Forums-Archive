---
title: "Title bar disappears suddenly when Compiz is enabled"
date: 2012-02-16
forum: Desktop Environments
---

### Post by NewUserFF on 2012-02-16
I am running Lubuntu 11.10, today i installed compiz, when i tried to run compiz using the command _compiz --replace_, the title bar and the taskbar disappeared. after studying it for a while, i found it may have some connection with _window decoration_( i have picked it in the ccms), when i try to start _window decoration_ in the command line ,i can find some information like: _Window manager warning: Failed to load theme "Ambiance": Failed to find a valid file for theme Ambiance_, it seems that the theme "Ambiance" isnt compatible with Window Decoration. i tried various themes, but nothing helps. Such information again. Can any one give a hand to me? any help appreciated.;)

---

### Post by NewUserFF on 2012-02-16
just now i found that, when i checked on the Animations Add-on, my lubuntu will crash, its the funtion that cause the problem. but why? any help? thx a lot !

---

### Post by NewUserFF on 2012-02-16
some animations adds-on caused the problems, close the crash animation, then everything is ok.

---

### Post by Rodney9 on 2012-02-17
I don't use compiz, but this might help you - 

[(Solved)How to enable compositing in Lubuntu.]("http://ubuntuforums.org/showthread.php?t=1856701")

For How-To's, Information and Screen-Casts on Lubuntu go to the
Lubuntu One Stop Thread - 

[[COLOR="Blue"]Lubuntu One Stop Thread[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1844755")

Rodney

---

### Post by mcduck on 2012-02-17
> **NewUserFF said:**
> I am running Lubuntu 11.10, today i installed compiz, when i tried to run compiz using the command _compiz --replace_, the title bar and the taskbar disappeared. after studying it for a while, i found it may have some connection with _window decoration_( i have picked it in the ccms), when i try to start _window decoration_ in the command line ,i can find some information like: _Window manager warning: Failed to load theme "Ambiance": Failed to find a valid file for theme Ambiance_, it seems that the theme "Ambiance" isnt compatible with Window Decoration. i tried various themes, but nothing helps. Such information again. Can any one give a hand to me? any help appreciated.;)

Ambiance theme sure is compatible with Compiz, the question here is  do you actually have the Ambiance Metacity theme installed (since you are using Lubuntu, which doesn't use Metacity by default)? And also you'll probably have to do something to help Compiz find the theme, as it would normally pick the theme to use from Gnome's configurations...

---

