---
title: "Installing Gnome apps without installing all of Gnome"
date: 2006-07-01
forum: Desktop Environments
---

### Post by blacknyx on 2006-07-01
Okay I'm using Xubuntu, without Gnome or KDE.

I however want to use Listen Media Player.
I decided that with the programs I need that have to be either Gnome or KDE I'd go with Gnome because it's lighter.

But with Listen downloaded using Automatix, it now says I need "bonobo" which is a Gnome application.

So how do I install a particular application for a different GUI without installing more than what's necessary??

Hope that makes sense.. thanks

---

### Post by greyhat on 2006-07-01
Command line apt-get or any apt package manager should get the bare minimum of required components to run non-native-to-your-window-manager programs, and nothing more, generally speaking...

If Listen says it needs bonobo, you could try just installing that and seeing what that does, or what packages installing bonobo would also get. 

Hopefully this helps!

---

### Post by adwait on 2006-07-01
Just install the program that you want via apt-get or any of the package managers and it will automatically install all dependencies.

---

### Post by gosh on 2006-08-12
I have the same problem.

I installed Listen with apt-get install.
Running Listen in a terminal says: 
```
Traceback (most recent call last):
  File "/usr/bin/listen", line 40, in ?
    import bonobo
ImportError: No module named bonobo

``` The same error appears after apt-get install bonobo

---

### Post by gosh on 2006-08-12
Just found out that installing Listen with aptitude in stead of apt-get does get it to work!

---

