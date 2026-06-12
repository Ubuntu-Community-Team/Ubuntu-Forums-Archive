---
title: "Workspace Backgrounds &amp; Screensaver"
date: 2006-07-17
forum: Desktop Environments
---

### Post by SPlutard on 2006-07-17
Is it possible to have a different background picture for each workspace?

Also, what happened to all the customizable features for the screensaver (like slideshows of pictures) - where can I set those options? Things are different with Dapper....

---

### Post by T700 on 2006-07-17
"Is it possible to have a different background picture for each workspace?"

Not with Gnome, although I've heard there may be a third party app that will do so.  I use KDE and that is an option.

Paul

---

### Post by asplode on 2006-07-17
I'm not sure of a program for the backgrounds, but [this thread]("http://ubuntuforums.org/showthread.php?t=198809&highlight=screensaver") might help out in the screensaver department.

I heard (or read) somewhere that the gnome development team decided that any screensaver that needed options was 'broken' and removed all reference to all but the most basic of options.

---

### Post by SPlutard on 2006-07-17
What's the difference between Gnome & KDE? I've heard that Gnome is more Windows-like and KDE is more Mac-like; is that true? Is it possible to switch without totally reinstalling Linux?

---

### Post by T700 on 2006-07-17
> **SPlutard said:**
> What's the difference between Gnome & KDE? I've heard that Gnome is more Windows-like and KDE is more Mac-like; is that true? Is it possible to switch without totally reinstalling Linux?

They are just two different window managers that work with Ubuntu Linux to bring you your graphical interface.  Linux can be run perfectly well from the command line only, but most people prefer on the desktop (versus a server) to have a graphical interface.

Think of KDE and Gnome as Ford and Chevy.  Both make cars that can take you to the market, but each company emphasizes certain features and has a slightly different market audience.  You can run one, two, or many windows managers.  My main box has Gnome, KDE, Icewm, and Fluxbox, but I like and use KDE 99% of the time.

Paul

---

### Post by SPlutard on 2006-07-17
Is there a tutorial/site I can check out so I can run KDE on top of my Gnome? The friend who got me interested in Linux in the first place is really urging me to use KDE over Gnome, so I'd like ot try it out.

---

### Post by jordilin on 2006-07-17
> **SPlutard said:**
> Is it possible to have a different background picture for each workspace?
It is not possible in Gnome, but possible in kde. If you wanna try kde, just go to synaptic and install kubuntu-desktop and you'll be able to switch between desktop managers at the login entry.

---

### Post by T700 on 2006-07-17
If you do decide to try KDE (I suggest it as the best way to really see the differences), here's the way I'd do it.  At a terminal, type:

```
sudo aptitude update
```

Press Enter.  Then:

```
sudo aptitude install kubuntu-desktop
```

Using Aptitude to install it will greaty simplify the uninstall process if you later decide you don't like it.

Paul

---

