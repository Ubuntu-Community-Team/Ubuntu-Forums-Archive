---
title: "Azureus, anyone?"
date: 2005-11-03
forum: Desktop Environments
---

### Post by kanton on 2005-11-03
Has anyone got Azureus to work flawlessly with any version of Ubuntu? I still get those errors with plugins and stuff -- on both my x86 and PPC). The main functions, i.d. the download part, seems to work properly.

Peter

---

### Post by Duncan_Idaho on 2005-11-03
ti runned flawlessly in hoary for me

---

### Post by Xian on 2005-11-03
Did you use the forum guide for [Installing Azureus](http://ubuntuforums.org/showthread.php?t=75272)?
The application works fine for me on Breezy.

---

### Post by flower on 2005-11-03
I'm using azureus on my breezy, and I did with hoary too ... 
Maybe if you post some of the error you've you can get a solution.

---

### Post by Joey French on 2005-11-03
Mine works, but I fought it from the repos, then installed it from the .deb on their site. Now, everytime it starts, it tries to upgrade/ download a file that it already has. But, it does work. I would not suggest the Azureus in the repos, it has problems.

---

### Post by flower on 2005-11-03
well ... you better have a look at : [http://ubuntuguide.org/](http://ubuntuguide.org/)
it's a beautiful piece of guide ... it'll help you for lot of stuff

---

### Post by kanton on 2005-11-03
[QUOTE=flower]well ... you better have a look at : [http://ubuntuguide.org/](http://ubuntuguide.org/)
it's a beautiful piece of guide ... it'll help you for lot of stuff[/QUOTE]

Well, it ain't as easy as it looks at Ubuntuguide -- at least not on any system I've tried to install it on. I get the errors in Azureus when I use the regular apt-get from the multiverse/universe repositories. Seems like it should work if I download the deb package from Azureus' page though. I'll better try it.

The problem is that it keeps complaining about missing plugins that are actually installed (and even impossible to uninstall).

Anyway, this ought to be marked as a bug in amongst the universe/multiverse repositories.

---

### Post by binarymelon on 2005-11-03
I was getting the errors and the way I got it working was:

Install Java using the PLF repositories:
[http://wiki.ubuntu-fr.org/doc/plf](http://wiki.ubuntu-fr.org/doc/plf)

```
sudo update-alternatives --config java
wget http://heanet.dl.sourceforge.net/sourceforge/azureus/Azureus_2.2.0.2_linux.GTK.tar.bz2
sudo mv Azureus_2.2.0.2_linux.GTK.tar.bz2 /opt
cd /opt
sudo tar xvf Azureus_2.2.0.2_linux.GTK.tar.bz2
sudo chown your_username:your_username azureus

```

Use smeg and create a menu option for azureus, the command is /opt/azureus/azureus

Once that is done just launch Azureus and let it update itself.

This is not guaranteed to work, but it worked for me

---

