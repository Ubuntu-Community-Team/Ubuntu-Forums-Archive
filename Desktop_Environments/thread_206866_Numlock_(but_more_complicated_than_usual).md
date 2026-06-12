---
title: "Numlock (but more complicated than usual)"
date: 2006-06-30
forum: Desktop Environments
---

### Post by ryanclem on 2006-06-30
Now before people get all uppity about someone else asking how to get numlock working, I've already installed automatix and numlockx.  My question is a bit deeper.  We are running a family computer with multiple users.  Numlock turns on at the Gnome log-in screen just fine, however once anyone other than ME logs in, it turns itself off.  I, for the life of me, can not figure out why I'm the only who who keeps numlock on once I log in.  In an attempt to figure it out I searched online and found this info at [http://ubuntuguide.org/wiki/Dapper:](http://ubuntuguide.org/wiki/Dapper:)

I should install numlockx and then find the file:

/etc/X11/gdm/Init/Default

and insert the following:

if [ -x /usr/bin/numlockx ]; then
 /usr/bin/numlockx on
fi

I have done all of this but it still only works for me.  I am not an Xpert (hahaha) at X or Gnome so I'm not entirely sure about the startup process for either.  I would absolutely love a detailed explination as to how I could run a program or script whenever anyone logs on or a link to a website where I could find some more information.  While I know I could just go and add numlockx as a startup command for each user, I'm really looking to figure out a method that's more systemwide.  What really gets me is that it only works for me, but I can't find any reference to numlockx in my home directory.  If anyone has any clue as to why it's only working for me that'd be awesome information to know too!  Thank you!

---

### Post by Dubbayoo on 2006-06-30
[QUOTE=ryanclem]Now before people get all uppity about someone else asking how to get numlock working, I've already installed automatix and numlockx.  My question is a bit deeper.  We are running a family computer with multiple users.  Numlock turns on at the Gnome log-in screen just fine, however once anyone other than ME logs in, it turns itself off.  I, for the life of me, can not figure out why I'm the only who who keeps numlock on once I log in.  In an attempt to figure it out I searched online and found this info at [http://ubuntuguide.org/wiki/Dapper:](http://ubuntuguide.org/wiki/Dapper:)

I should install numlockx and then find the file:

/etc/X11/gdm/Init/Default

and insert the following:

if [ -x /usr/bin/numlockx ]; then
 /usr/bin/numlockx on
fi

I have done all of this but it still only works for me.  I am not an Xpert (hahaha) at X or Gnome so I'm not entirely sure about the startup process for either.  I would absolutely love a detailed explination as to how I could run a program or script whenever anyone logs on or a link to a website where I could find some more information.  While I know I could just go and add numlockx as a startup command for each user, I'm really looking to figure out a method that's more systemwide.  What really gets me is that it only works for me, but I can't find any reference to numlockx in my home directory.  If anyone has any clue as to why it's only working for me that'd be awesome information to know too!  Thank you![/QUOTE]

You could set numlockx to start with everyone's session.

---

### Post by stalefries on 2006-07-31
I think he would like to know HOW to do that.

---

