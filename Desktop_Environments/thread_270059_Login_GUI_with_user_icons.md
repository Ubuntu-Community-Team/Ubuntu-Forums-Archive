---
title: "Login GUI with user icons"
date: 2006-10-02
forum: Desktop Environments
---

### Post by tracyapotter on 2006-10-02
Kubuntu - Dapper and/or Edgy

I have done it before, but now cannot repeat.  ](*,) 

My work systems have 3 users: a generic, a personal, and a guest that only can see the internet.

I need the login screen to have the three choices listed on the side with their respective icons.



   Welcome to ABC Company
    Please choose a User
:KS  Generic
8)   Personal
:-#  Guest



I have tried each of the GUI styles, but still logs into the generic Kubuntu login screen with the last user already filled in.

Does anyone know which of the GUI choices does this?

Thanks,

TA

---

### Post by an.echte.trilingue on 2006-10-07
I don't know of any KDM themes in the repositories that do that, but if you go to KDElook.org there are many there to that do what you want.  To install them simply unpack them and move the resulting folder to /usr/share/apps/kdm/themes/ and then you will be able to select it like any other; if the first one you download does not work, just try another one; for some reason some only work with certain distros/configurations.

Good Luck!

-mat

---

### Post by tracyapotter on 2007-01-04
I found the solution...

edit /etc/kde3/kdm/kdmrc (as root)

find the line that reads:

     UseTheme=true

and change to 

     UseTheme=false

Now you get a login screen that lists all of the users on your computer with their icons (all editable)

---

