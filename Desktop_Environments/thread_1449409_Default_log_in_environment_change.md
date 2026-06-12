---
title: "Default log in environment change"
date: 2010-04-07
forum: Desktop Environments
---

### Post by David D. on 2010-04-07
I added Kubuntu to Ubuntu, but accidentally selected Kubuntu as the default for login.  How do I change this to Ubuntu?

---

### Post by micio on 2010-04-08
I don't understand if you replaced kdm with gdm, in anycase in the display manages options there is the switch to change desktop environment.

Bye 

Micio

---

### Post by Nipas on 2010-04-08
Run 
dpkg-reconfigure gdm . This is possibly what you have to do ;)

---

### Post by shaka_zulu on 2010-04-08
I believe that you have added KDE environment to GNOME environment. Read more about differences [here]("http://www.ubuntu-how-to.com/2010/04/what-is-gnome-kde-and-xfce.html"). Generally it is very simple. Once upon you restart your computer and it reaches log in screen there is a side button which you should click and choose GNOME and then type username and password. This will be remembered so next time GNOME will be your default GUI. Your default GUI is always your last session environment. 

Enjoy

---

