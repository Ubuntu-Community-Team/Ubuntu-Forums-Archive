---
title: "Openbox on startup"
date: 2011-03-10
forum: Desktop Environments
---

### Post by nilosweden on 2011-03-10
Hey guys. Im going crazy soon.

I have installed openbox but i have a problem. When i type startx after i logged in, the bloody gnome starts up.

I've created .xsessionrc in my home directory and put exec openbox and some other settings. I can run the script and everything works beside openbox.

Getting a error: a desktop manager is already running on screen 0. (something like that).

I want to change the default desktop UI to openbox.
Ive changed the /usr/share/grub/default/grub to start the system in text mode instead of having the GUI loginscreen. Seems like my last session is not saved.

Any ideas?

---

### Post by kerry_s on 2011-03-10
so in gnome go to the login screen settings & select openbox as the default. then when you run startx it should do openbox.

---

### Post by nilosweden on 2011-03-10
ye i logged in, started the gdm, logged out and pressed F7 to login the usual way but i can't login that way either. i can only login when chosing Gnome desktop...

i also changed the session key with gconf-editor in /desktop/gnome/session/required_components/windowmanager but still nothing.

The wierd thing is that its seems like im running openbox and (whats the name of the default desktopmanager in ubuntu?) and that one...

---

### Post by kerry_s on 2011-03-10
> whats the name of the default desktopmanager in ubuntu?

it's metacity. only 1 window manager can run at a time.
if you changed it in gconf-editor, then your running mixed, as in openbox-gnome.

if you want a more openbox system, i suggest you go lubuntu:
[http://people.ubuntu.com/~gilir/lubuntu-10.10.iso](http://people.ubuntu.com/~gilir/lubuntu-10.10.iso)

lubuntu is openbox with a panel & other creature comforts.

---

