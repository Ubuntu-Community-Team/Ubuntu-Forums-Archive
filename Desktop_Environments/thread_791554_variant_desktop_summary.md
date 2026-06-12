---
title: "variant desktop summary"
date: 2008-05-12
forum: Desktop Environments
---

### Post by thefamousnomo on 2008-05-12
hello people

just wondering if anyone can point me in a general summary of all variant desktop enviroments and their default components?

i.e.
ubuntu
gnome desktop enviroment
gdm login manager
metacity window manager
nautilus file manager

and then perhaps some alternatives..? and maybe some sort of explanation as to what the composite window managers are and how they interact with the desktop enviroment please? this is just for my own info but a few friends whom i have converted would be interested also.

cant seem to find anything definitive anywhere, might make a good sticky..?

thanks vmuch

thefamousnomo

---

### Post by Xiong Chiamiov on 2008-05-13
As far as Desktop Environments go, GNOME and KDE are the big two, followed by Fluxbox, XFCE, JWM... there's a nice comparison [on Wikipedia]("http://en.wikipedia.org/wiki/Comparison_of_window_managers"), of course.

My experience is mostly with KDE, which has 2 file managers.  Dolphin is the new, light-weight one, though it has some [weird]("https://bugs.launchpad.net/ubuntu/+source/dolphin/+bug/152788") [problems]("https://bugs.launchpad.net/ubuntu/+source/dolphin/+bug/156002").  Konqueror is more full-featured and stable, but can be a hog sometimes.

---

### Post by thefamousnomo on 2008-05-13
> **Xiong Chiamiov said:**
> As far as Desktop Environments go, GNOME and KDE are the big two, followed by Fluxbox, XFCE, JWM... there's a nice comparison [on Wikipedia]("http://en.wikipedia.org/wiki/Comparison_of_window_managers"), of course.

this is where i get a bit confused... are fluxbox, xfce, et al not window managers..? and my understanding was that gnome had a window manager called metacity, kdes called kwin... which leaves the question - what are gnome / kde in terms of desktop enviroment component (my thoughts were that they were a default set of components that work well together..?)

thanks for your thoughts, what is your take on the above?

---

### Post by aanderse on 2008-05-13
desktop environments are usually comprised of the following core components:
[LIST]
[*]window manager
[*]session manager
[*]file manager
[*]desktop manager
[*]settings daemon
[*]panel
[/LIST]

a traditional desktop provides all of these components. for example with gnome you have: metacity window manager, gnome-session as session manager, nautilus as file manager, nautilus also manages the desktop, gnome settings daemon, and gnome-panel as the panel. xfce on the other hand has the following software: xfwm4 as window manager, xfce4-session as session manager, thunar as file manager, xfdesktop4 as desktop manager, xfce4-session as session manager, and xfce4-panel as the panel... so xfce is not a window manager (xfwm4 is), xfce is a desktop environment.

i'm not sure about JWM. i believe it is just a window manager, but i also think it usually ships with a desktop manager and panel which were designed for JWM.

hope this helps you understand....

---

### Post by thefamousnomo on 2008-05-13
yes, this is more like it... so aanderse, are you able to throw up a summary for all ubuntu variants x/k/ubuntu, maybe with a wee bit more info with regard to each component and what they control? (BTW, what about login managers?)

also, where do composite window managers fit in..? my understanding is that they work with the window manager present, so are not really full window managers..?

---

### Post by thefamousnomo on 2008-05-16
* bump *

cmon guys, this is how we learn...

would really appreciate...

---

### Post by Xiong Chiamiov on 2008-05-17
What exactly are you wanting to know?
Ubuntu uses GNOME, Kubuntu uses KDE, and Xubuntu uses XFCE, at least by default.  There are login managers for each one, though of course you could use any, or just the plain X login.

---

### Post by thefamousnomo on 2008-05-19
> **aanderse said:**
> desktop environments are usually comprised of the following core components:
[LIST]
[*]window manager
[*]session manager
[*]file manager
[*]desktop manager
[*]settings daemon
[*]panel
[/LIST]

a traditional desktop provides all of these components. for example with gnome you have: metacity window manager, gnome-session as session manager, nautilus as file manager, nautilus also manages the desktop, gnome settings daemon, and gnome-panel as the panel. xfce on the other hand has the following software: xfwm4 as window manager, xfce4-session as session manager, thunar as file manager, xfdesktop4 as desktop manager, xfce4-session as session manager, and xfce4-panel as the panel... so xfce is not a window manager (xfwm4 is), xfce is a desktop environment.

i'm not sure about JWM. i believe it is just a window manager, but i also think it usually ships with a desktop manager and panel which were designed for JWM.

hope this helps you understand....

sorry, thought it was really clear what i was asking... i know that ubuntu uses gnome, kubuntu uses kde, xubuntu uses xfce but please read the above quote. i would like a summary of all of the default components for the 3 main variants. the above doesnt mention login managers or kubuntu, or composite window managers and how they work.

i have read this thread over and over, cant see how you missed the question... i started the thread with it and have even had it answered to an extent. i simply want to learn, so i seek information, and i was hoping that this would be the place to find it. aanderse has already helped but a full summary would be handy to link to.

---

### Post by thefamousnomo on 2008-05-21
* bump *

im sure someone must be able to summarise the above or at least point me to a summary (google cant help).

---

### Post by aanderse on 2008-05-25
i've attached a document with some tables explaining some stuff.
you're not the only person to have these questions... if any user is coming to gnu/linux from windows this can be a pretty confusing topic. with windows there are no alternatives, so you just see the desktop environment as one thing (when infact it is not).

maybe someone should take this information, clean it up, and put it up on a wiki?

hope this helps you. if any point needs clarification just ask.

---

### Post by thefamousnomo on 2008-05-26
> **aanderse said:**
> i've attached a document with some tables explaining some stuff.
you're not the only person to have these questions... if any user is coming to gnu/linux from windows this can be a pretty confusing topic. with windows there are no alternatives, so you just see the desktop environment as one thing (when infact it is not).

agreed, nice one... exactly what i was looking for.

> **aanderse said:**
> maybe someone should take this information, clean it up, and put it up on a wiki?

all for this

thanks again

---

