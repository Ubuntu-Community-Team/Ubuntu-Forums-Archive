---
title: "Top bar menus"
date: 2012-04-08
forum: Desktop Environments
---

### Post by raysa on 2012-04-08
How can I make the top bar menus of applications appear in the app windows instead of at the very top of the screen? (Ubuntu 11.10).
If an app window is placed bottom right of the screen, it seems daft to have its menu separated and placed way up top left, but that seems to be the default??

Any thoughts on this? Surely not everyone finds it logical to have the menu bar completely separated from the application window it relates to, especially as it isn't even visible unless you take the curser out of the app window and go to the top of the screen to see it?

---

### Post by squilookle on 2012-04-08
It depends on what you are used to and what you like. Personally, I don't like having the menu where it is in Unity (but I use other DEs so it does not affect me) but there are others that like having them there. Mac users have had the menu of the top left of the screen for a very long time, and KDE users have had the option for a long time too. 
 
The main point though, is that there seems to be a roadmap/agenda in the changes that have been occuring in Ubuntu over the last few versions, with the introduction of things like the HUD. You may not like the changes now, but I believe they know what they are doing, and are leading somewhere (looking at the bigger picture). 
 
I'm not sure of a way to go back to the menus appearing in the windows in Unity, but you could always try another DE. KDE, XFCE, LXDE Gnome Shell all currently give you that option, but each offer you a different experience and required varying amounts of system resources, so I'm sure you can find something you like there, and you won't have to switch OS.

---

### Post by raysa on 2012-04-08
Oh, I was hoping there was an adjustment that could be made by way of customising.

One of the things I really liked about Ubuntu with I first came to it some years ago was that I could easily customise it just as I wanted - with my own tailored menus, layouts etc.

If it's now going down the route of "We know what you need and this is how it will be, take it or leave it," isn't that what we all hate about MS Windows? 

The ability to customise is a key part of user satisfaction. Without it I might as well just buy a standard box from Tesco, plug it in and go with MS.

---

### Post by squilookle on 2012-04-08
> **raysa said:**
> Oh, I was hoping there was an adjustment that could be made by way of customising.

One of the things I really liked about Ubuntu with I first came to it some years ago was that I could easily customise it just as I wanted - with my own tailored menus, layouts etc.

If it's now going down the route of "We know what you need and this is how it will be, take it or leave it," isn't that what we all hate about MS Windows? 

The ability to customise is a key part of user satisfaction. Without it I might as well just buy a standard box from Tesco, plug it in and go with MS.

You can still customize to your hearts content, you just may have to install another deskttop to do so. This is easily done and is like installing any other software package. 

MS Windows does not let you do that.

---

### Post by Krytarik on 2012-04-08
> **raysa said:**
> How can I make the top bar menus of applications appear in the app windows instead of at the very top of the screen?
To disable Global Menu in all sessions, run:
```
echo 'unset UBUNTU_MENUPROXY' | sudo tee /etc/X11/Xsession.d/81ubuntu-menu-proxy
```
You need to relogin for the change to take effect. If you want to revert that later, just remove the created file.

Regards.

---

### Post by raysa on 2012-04-09
Thanks Krytarik, but I've tried this and rebooted and it doesn't seem to work. I've looked in the /etc/X11/Xsession.d folder and the 81ubuntu-menu-proxy file is there but in a text reader it appears empty. Is there anything else I need to do?

Thanks also squilookle. Can I change desktop without having to reinstall all my software, settings, etc? The Ubuntu website doesn't seem to offer alternative desktops - are they completely new installations or just gui changes?

Discovered the answer to my last question.
Seems the desktops are just top-layer graphic choices and leave all the stuff underneath in place.
Just installed KDE and xubuntu. My, what a lot to play with and customise!

---

### Post by Krytarik on 2012-04-09
> **raysa said:**
> Thanks Krytarik, but I've tried this and rebooted and it doesn't seem to work. I've looked in the /etc/X11/Xsession.d folder and the 81ubuntu-menu-proxy file is there but in a text reader it appears empty.
Make sure to copy & paste the entire command, or alternatively, enter it correctly.

---

### Post by squilookle on 2012-04-10
> **raysa said:**
> Discovered the answer to my last question.
Seems the desktops are just top-layer graphic choices and leave all the stuff underneath in place.
Just installed KDE and xubuntu. My, what a lot to play with and customise!

Hi raysa, 

You are right, it leaves the underlying system in tact. Glad you find the answer, hope you're enjoying playing with and customizing the other desktops, and that you can get your computer set up how you want it.  :)

---

### Post by raysa on 2012-04-11
One more question please. I'm confused between the terms KDE and kubuntu. Are they just different terms for the same thing?
I installed KDE plasma from the software centre (and so far really like it) - does this mean I am using kubuntu, or is that something different?

---

### Post by kiirokurisu on 2012-04-12
Kubuntu is a variant of Ubuntu that has all the KDE pieces pre-installed so you get a nice KDE desktop out of the box. You can achieve pretty much the same effect if you have installed Ubuntu by installing the kubuntu-desktop package.

---

