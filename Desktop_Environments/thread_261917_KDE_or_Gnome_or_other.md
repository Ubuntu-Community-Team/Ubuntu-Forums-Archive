---
title: "KDE or Gnome or other?"
date: 2006-09-20
forum: Desktop Environments
---

### Post by liquilife on 2006-09-20
Hello. I've been working under Ubuntu for almost a week now. I feel like I am figuring things out pretty quickly. But as Einstein once quoted "The more you know, the more you know you DO NOT know". This is the case regarding desktop environments. It's become painfully obvious as I get ready for some heavy customizations in Ubuntu that I will have needed to decide on one or the other or maybe there is another desktop environment that is more suited for m e, I just do not know!

This is what I've observed thus far:

Gnome seems to look better on all aplications. I personally love the brown theme and the overall general feel. I do have a few issues. It seems difficult to get anything to add to my Applications menu. I can't seem to get Gaim to auto start. It seems to lack in a fast production environment in the GUI area. Perhaps this is because I'm very new. I don't know. I love the font that is used in this form field I'm typing in. What font is it btw??

KDE looks spectacular on programs designed for the KDE environement but seems to be really 'blah' on any programs not designed specifically for the KDE environement. KDE runs Gaim on startup on it's own. I can navigate quite well as well and it seems customizing is within my capability without too much confusion and research. It seems more userfriendly to the new user who has that geekish touch already. I don't like the theme setup. Probably sounds crazy as that is surely a selling point for KDE. Maybe it's because most KDE themes have been replicated on Windows and I've seen it so much I've grown tiresome of it.

I just am not sure which one to stick with. Switching back and forth is just not very productive at all while I'm deciding. Is there a Ubuntu default Knome theme for KDE? :D

Are there other Desktop Environments worth checking out? What do you think?

Sorry, this turned into an essay!

---

### Post by someguyouknow on 2006-09-20
you can try out Xfce, Fluxbox, Enlightentment, etc.

i myself love KDE... i tried Gnome and hated it...

---

### Post by aysiu on 2006-09-20
You can switch back and forth much more quickly by installing *xnest* ```
sudo aptitude update
sudo aptitude install xnest
``` and then using this command ```
gdmflexiserver --xnest
``` to log into the other desktop environment simultaneously.

---

### Post by gils0040 on 2006-09-21
to get gaim to startup automatically in gnome go to System -> Sessions -> Startup Programs and add gaim. As for deciding which environment to use, i went through the same thing. started out with kde and eventually switched to gnome. gnome just seems so much simpler to me. remember you can customize either to act and feel however you would like. good luck!

---

### Post by liquilife on 2006-09-21
Thank you! You know what? I think I'm pretty stuck on KDE. I'm pretty hooked to SuperKaramba already just after a few hours of using it :)

I still love the human theme for Knome and would kill to have some time of port over to KDE as a theme/style.

---

### Post by chavo on 2006-09-21
Go to [http://kde-look.org](http://kde-look.org), there are a couple of color schemes that mimic the Ubuntu Human theme.

 Also make sure you install the QTCurve kdestyle, with it you can replicate the Ubuntulooks gtk-engine. It is a very configurable style though it's not just made to replicate the gtk-engine. It also has a Gtk-theme so you can have your gtk apps match your kde style. It works much better than the gtk-qt engine. It's just a great style for both desktops and pretty much the only one I use anymore. There are kubuntu .debs on kde-look.org.

---

### Post by puppy on 2006-09-21
I use the Gnome environment almost exclusively, but have Amarok installed for my music files, and also Kaffeine because of it's 'easy to install' Digital TV interface, so you can mix and match your applications if you want to. The KDE apps will grab the dependant KDE libs they require (quite a few of them) when you select them to install through Synaptic, but with the above two apps the entire KDE environment won't be installed as well (that's not true with all KDE apps mind you, so best to see what dependencies new applications want to bring along with them - you might want a small network analyser and get the entire KDE desktop for your troubles :razz:  )

---

