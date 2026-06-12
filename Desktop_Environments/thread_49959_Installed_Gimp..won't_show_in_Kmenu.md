---
title: "Installed Gimp..won't show in Kmenu"
date: 2005-07-18
forum: Desktop Environments
---

### Post by coolblue on 2005-07-18
Hi
I installed Gimp via Kynaptic by adding Ubuntu CD.
And then Firefox manually with its latest installer.tar.gz from its website.
After install, Firefox popped up instantly.

But neither Firefox nor Gimp can I find in Kmenu.
When I run command Gimp, it starts but I want it in Kmenu.
The run command firefox does nothing.

Plz help

Thanks

---

### Post by damonw5 on 2005-07-18
[QUOTE=coolblue]Hi
I installed Gimp via Kynaptic by adding Ubuntu CD.
And then Firefox manually with its latest installer.tar.gz from its website.
After install, Firefox popped up instantly.

But neither Firefox nor Gimp can I find in Kmenu.
When I run command Gimp, it starts but I want it in Kmenu.
The run command firefox does nothing.

Plz help

Thanks[/QUOTE]
 Try editing the K menu. I believe you can right-click on it to add to it. If not, there should be a menu editor in the "Control Center". When you create a new shortcut/launcher/whatever, for gimp have it run "/usr/bin/gimp" . I'm not sure where the manual firefox install goes, but you could look in your home directory or try "/usr/bin firefox" .

---

### Post by GeneralZod on 2005-07-18
Strange about The GIMP - mine showed up straight away under

 Graphics-> Image Editor (GIMP Image Editor)

Try running 

kappfinder

and see if it turns up.

---

### Post by coolblue on 2005-07-19
[QUOTE=GeneralZod]Strange about The GIMP - mine showed up straight away under

 Graphics-> Image Editor (GIMP Image Editor)

Try running 

kappfinder

and see if it turns up.[/QUOTE]
 Thanks, Gimp showed up as well as Xeyes and Nano which I didn't know were there.
By the way firefox is in my home...how do i get it to my menu?

---

### Post by Altmenorg on 2005-07-19
[QUOTE=coolblue]Hi
I installed Gimp via Kynaptic by adding Ubuntu CD.
And then Firefox manually with its latest installer.tar.gz from its website.
After install, Firefox popped up instantly.

But neither Firefox nor Gimp can I find in Kmenu.
When I run command Gimp, it starts but I want it in Kmenu.
The run command firefox does nothing.

Plz help

Thanks[/QUOTE]
 Yes, because they are Gnome applications, you may create the links manually...
That sometimes happened unless the developper/packager has anticipated the possible installation over a KDE desktop...
I also suggest to install Krita, a good Gimp alternative for KDE, very recent app, that needs improvement, but is quite usable for its first release !!!

You may need to add this repo to your sources.list file :

deb [http://kubuntu.org/hoary-koffice14/](http://kubuntu.org/hoary-koffice14/) hoary-updates main

I generally suggest to use QT apps on a KDE desktop as well as GTK apps on Gnome, simply for performances reasons...

Personnal wish : we need a good QT browser !!!! (not that khtml is not a good engine, but konqueror has very, very little options for the web...)

Hope this helps ;)

---

### Post by tmmuk on 2005-09-30
how can I get flightgear to show up in the kmenu?

btw kappfinder doesn't find it, and a reboot doesnt work either

---

