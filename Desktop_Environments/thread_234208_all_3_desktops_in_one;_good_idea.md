---
title: "all 3 desktops in one; good idea?"
date: 2006-08-11
forum: Desktop Environments
---

### Post by maniacmusician on 2006-08-11
is it a good idea (or rather, is it a bad idea) to have all 3 desktop environments installed (Gnome, KDE, XFCE). I did this on impulse, and I have to say, my menu is looking kind of cluttered. are there any adverse affects? 

if i remove kubuntu-desktop and ubuntu-desktop, will that cause any dependency problems?

thanks.

---

### Post by Lunar_Lamp on 2006-08-11
Well, unless you installed them using aptitude it won't do anything.  Those are just meta-packages and removing them won't do anything.

---

### Post by maniacmusician on 2006-08-11
oh. so how would i remove Gnome and KDE? and would that create any dependency problems?

---

### Post by petersjm on 2006-08-11
If you installed kubuntu-desktop using

```
sudo aptitude install kubuntu-desktop
```

and said yes when it told you it wanted to install a bazillion (that's a real word!) dependencies, then you can uninstall everything in the same way:

```
sudo aptitude purge kubuntu-desktop
```

This will delete all dependencies, too.

I'm not sure if you can use aptitude to remove/purge if you used apt-get to install... (?)

---

### Post by maniacmusician on 2006-08-11
lol are you telling me there's no other way to get rid of ubuntu and kubuntu besides using aptitude? and I did use apt-get to install it, so dont even know if aptitude will even remove it. 

does anyone else know another way?

---

### Post by ardchoille on 2006-08-11
> **maniacmusician said:**
> is it a good idea (or rather, is it a bad idea) to have all 3 desktop environments installed (Gnome, KDE, XFCE). I did this on impulse, and I have to say, my menu is looking kind of cluttered. are there any adverse affects? 

if i remove kubuntu-desktop and ubuntu-desktop, will that cause any dependency problems?

thanks.

**About your menus:**
You can control which items appear in which menus by telling the .desktop files in /usr/share/applications which menus to appear in. I noticed that some KDE apps have menu items (.desktop files) that have a line like this

OnlyShowIn=KDE

which would make those menu items appear only in the kde menus and not the gnome menus. You can change the menu items and add that line to some items so they will only appear in certain desktops' menus.
You can open a term and do: [COLOR="Red"]grep -r Show /usr/share/applications/[/COLOR]  to see what I mean.

**About removing KDE or gnome:**
Aptitude tracks things you have installed with aptitude and will uninstall the apps and their deps. Aptitude won't be able to help with that if you installed packages with apt-get.

Have a look at the "Pure *" links at this page:

[http://www.psychocats.net/ubuntu/index.php](http://www.psychocats.net/ubuntu/index.php)

This tells which apps you need to uninstall to return to certain desktop environments.

---

### Post by maniacmusician on 2006-08-12
hey thanks a bunch for that link and the useful info about the menus...i will certainly try that later. my system is a bit of a mess and i'm trying to fix it right now. could be days or weeks, no idea. hut thank you very much for the reply. If i can fix the cluttered menus i will probably not need to uninstall them.

---

### Post by ardchoille on 2006-08-12
> **maniacmusician said:**
> hey thanks a bunch for that link and the useful info about the menus...i will certainly try that later. my system is a bit of a mess and i'm trying to fix it right now. could be days or weeks, no idea. hut thank you very much for the reply. If i can fix the cluttered menus i will probably not need to uninstall them.

You're very welcome. And, if you find a better way to manage the menus for multiple desktops, be sure and let us know.

---

### Post by maniacmusician on 2006-08-13
I don't think I'll get to...I was getting a little impatient with my problem, so i've decided to reinstall Xubuntu. it was a pretty serious problem. Wouldn't let me log in, so i had to boot in recovery mode and use startx to get an active X session. but its not healthy to run for days at a time as root, so i thought i'd better just reinstall. Next time, I don't think i'll be installing all three desktops, but I might install programs from different desktops to run on Xubuntu. Do you know how much this will affect performance? I mean, I know it will bring dependencies, but what kind of a hit will my performance take? Xubuntu is usually super fast.

thanks

---

