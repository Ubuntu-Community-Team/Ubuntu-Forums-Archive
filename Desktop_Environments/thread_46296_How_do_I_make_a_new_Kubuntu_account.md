---
title: "How do I make a new Kubuntu account?"
date: 2005-07-04
forum: Desktop Environments
---

### Post by arcanistherogue on 2005-07-04
I have just installed the packages via the apt-get install command in Ubuntu's command line.  I set KDE as the default desktop manager, and on bootup it went to a really nice login screen.  I typed in my Ubuntu name and password and it booted up GNOME.  Do I need to make a new account to use Kubuntu?

If so, how do I do this if I can't even log in?

---

### Post by frodon on 2005-07-04
Users definition is independant of the graphical  interface (gnome, kde, xfce, ...), so you don't need to create a new user account but it could be an idea to create an user for each ... why not !
If you want to create new user (in gnome) just go to System > Administration>user or use a terminal and the useradd command (useradd --help if you want some help).

---

### Post by Sye d'Burns on 2005-07-04
Just a thought, but did you change your session type when you logged in?

---

### Post by arcanistherogue on 2005-07-04
Oh, so I can use this in KDE?  Then how do I stop this account from booting GNOME, I want it to boot KDE.

---

### Post by arcanistherogue on 2005-07-04
[QUOTE=Sye d'Burns]Just a thought, but did you change your session type when you logged in?[/QUOTE]
...to be frank, I don't know. I'm rather new to Linux.

---

### Post by Sye d'Burns on 2005-07-04
Try looking around on the sign in screen. On gdm it's 'sessions'... I'm not sure what kdm has it named.

---

### Post by arcanistherogue on 2005-07-04
Dear God, it worked.  I thank you.

KDE is bueatiful.

---

### Post by Sye d'Burns on 2005-07-04
Glad it worked, enjoy!

---

### Post by frodon on 2005-07-04
Your account not boot on GNOME, when are in the login screen click on session and choose KDE it will ask you if you want to set KDE as default session after login.
Other .... if you prefer KDE than gnome give a try to XFCE.

---

