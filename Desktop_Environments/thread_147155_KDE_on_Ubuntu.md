---
title: "KDE on Ubuntu"
date: 2006-03-19
forum: Desktop Environments
---

### Post by Kersus on 2006-03-19
If I have Ubuntu is there a way to add KDE to it easily and have the option at bootup whether I want gnome or kde?

---

### Post by gryphn on 2006-03-19
add all the packages trough APT and apply, then on the logon screen choose KDE as a session nad select default, 

make sure all repositores are up to date. 

BTW KDE 3.4 is prety and works really well,

---

### Post by Adrian on 2006-03-19
[QUOTE=Kersus]If I have Ubuntu is there a way to add KDE to it easily and have the option at bootup whether I want gnome or kde?[/QUOTE]

Sure. Just install the **kubuntu-desktop** package.

```

sudo aptitude install kubuntu-desktop

```

(Note, if you use **aptitude** instead of **apt-get**, you will be able to remove the KDE desktop easily if you change your mind)

Anyway, when the package is installed, you will be able to choose desktop environment from the "Session" menu on the login screen.

---

### Post by Vasco Coelho on 2006-03-24
Hi. 
i just did exactly that and i get errors when entering kde things like :
"Could not start process Unable to create io-slave:
klauncher said: Unknown protocol 'system'"
and when send something to trash  :"Could not start process Unable to create io-slave:klauncher said: Unknown protocol 'trash'."

Any sugestions how can i get this up and running? thank's in advance

---

### Post by Adrian on 2006-03-25
[QUOTE=Vasco Coelho]
Any sugestions how can i get this up and running? thank's in advance[/QUOTE]

If you try to install it again, what messages do you get?

---

### Post by Vasco Coelho on 2006-03-27
Well i ended up instaling all again , using a kubunto cd from scratch and now it's perfect

---

