---
title: "Help Help !! Am I the only one with 11.10 dual monitor problems"
date: 2011-11-08
forum: Desktop Environments
---

### Post by J Blain on 2011-11-08
My first post on the matter shows that either I am the only one with dual monitor problems or that no one knows enough to solve this issue ??

Basically since moving my Alienware MX11 from 11.04 to 11.10, dual monitors (up to date NVIDIA drivers) in gnome classic have stopped working. I never had any problems with it before.

Now if I try to go dual (extended desktop) I get :

1) Both monitors recognised
2) My laptop computer shows my desktop
3) The external monitor shows all white background
4) Both desktop show a kind of generic and unusable menu that has nothing to do with the menu bar I normally get in single monitor mode.
5) I have no applets showing on the top right side of the screens

This is really really really annoying. I am sure that this is an easy fix for someone in the know...

I suspect that /etc/X11/xorg.conf is somehow not right ?

Any all help will be greatly appreciated

---

### Post by RavanH on 2011-11-08
Hi J, you are certainly not the only one with an Nvidia card and dual monitor problems. See [http://www.google.com/search?q=ubuntu+nvidia+driver+and+dual+monitor+problem](http://www.google.com/search?q=ubuntu+nvidia+driver+and+dual+monitor+problem) for instance...

Does your install still have a /etc/X11/xorg.conf file? If so, you must have always upgraded and never a clean install.. it might be worth the trouble starting with a clean install (you can use Deja-Dup to back up the files in your home directory) and then follow one of the tutorials out there to avoid any confusion.

I know it's not real helpful but it should get you closer to get it working.

---

