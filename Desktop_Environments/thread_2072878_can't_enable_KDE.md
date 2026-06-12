---
title: "can't enable KDE?"
date: 2012-10-18
forum: Desktop Environments
---

### Post by gandalf3 on 2012-10-18
i installed KDE by running
```
 sudo apt-get install kde-window-manager

```
in the terminal, but it's not listed in the drop down menu in the login screen.. :confused:
how do i start it?

---

### Post by kc1di on 2012-10-18
that because you need to install kubuntu if you want kde.
```
sudo apt-get install kubuntu-desktop
```
that will do it for you.

---

### Post by jerrrys on 2012-10-18
I do not run kde, but looks to me you have to load the kde-plasma-desktop or perhaps just the plasma-desktop.

[http://packages.ubuntu.com/precise/kde-plasma-desktop](http://packages.ubuntu.com/precise/kde-plasma-desktop)

[]("http://packages.ubuntu.com/oneiric/plasma-desktop")

---

### Post by deadflowr on 2012-10-18
> **gandalf3 said:**
> i installed KDE by running
```
 sudo apt-get install kde-window-manager

```
in the terminal, but it's not listed in the drop down menu in the login screen.. :confused:
how do i start it?

Yes, because KDE-window-manager aka kwin, is like compiz.
Follow the either of the previous post to get the desktop.
KDE is an environment, not a window manager. It consists of a whole host of packages and libraries.

---

### Post by gandalf3 on 2012-10-22
thanks..
:oops:
how did i miss that! :P

i noticed that this changed the splash screen that appears after booting from grub (i don't mind this because it was just blank 
pink/purple before, though i think it was supposed to have and Ubuntu logo on it.)
but now it has a Kubuntu logo, and since i'm just sort of giving KDE a trial run, (and now i know that splash screen can be changed)
is it possible to create a custom one? or at least get a working regular Ubuntu one?

also this changed the background colour in grub to a light grey that makes it hard to read the text with.. (though i never cared for the original pink anyway) is there a way to change the colour of that too?

Thanks in advance. :)

---

