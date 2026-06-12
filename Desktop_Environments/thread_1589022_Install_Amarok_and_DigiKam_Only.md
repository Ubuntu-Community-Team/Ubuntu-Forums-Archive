---
title: "Install Amarok and DigiKam Only"
date: 2010-10-05
forum: Desktop Environments
---

### Post by marty1011 on 2010-10-05
Hello,

I am trying to install Amarok and DigiKam. Every time I install them using apt-get I find that applications such as Dolphin, KPackageKit, Konqueror are automatically installed with these two applications. 

Is there a way to install only Amarok, DigiKam and the necessary dependencies? Thank you very much for your help.

---

### Post by glitch323 on 2010-10-05
I heard that's the problem with downloading KDE apps on Gnome or Gnome apps on KDE, all the dependencies.  I was just thinking I would like to have K3b and DigiKam on my Ubuntu box as well, so I'm interested in what others have to say.  I found this: [http://www.digikam.org/drupal/download?q=download/dependencies](http://www.digikam.org/drupal/download?q=download/dependencies)

---

### Post by SeijiSensei on 2010-10-07
Take a look at this thread: [http://ubuntuforums.org/showthread.php?t=1588950](http://ubuntuforums.org/showthread.php?t=1588950)

You can use --no-install-recommends or remove konqueror, et. al., after the installation.

There's no way you can install a KDE application without a considerable number of dependent libraries being installed as well.  I have the same experience when I install a GNOME app like Synaptic or Gnumeric on my KDE box.

---

### Post by glitch323 on 2010-10-07
> **SeijiSensei said:**
> Take a look at this thread: [http://ubuntuforums.org/showthread.php?t=1588950](http://ubuntuforums.org/showthread.php?t=1588950)

You can use --no-install-recommends or remove konqueror, et. al., after the installation.

There's no way you can install a KDE application without a considerable number of dependent libraries being installed as well.  I have the same experience when I install a GNOME app like Synaptic or Gnumeric on my KDE box.

Ah, that's a good idea.  Thanks for that!  Although, the more I use KDE, the more I like it.  I'm torn between the two right now, so I don't mind having both installed on my main computer.  For my old and slow laptop though, this should really help.

---

### Post by Fri13 on 2010-10-07
> **marty1011 said:**
> Hello,

I am trying to install Amarok and DigiKam. Every time I install them using apt-get I find that applications such as Dolphin, KPackageKit, Konqueror are automatically installed with these two applications. 

Is there a way to install only Amarok, DigiKam and the necessary dependencies? Thank you very much for your help.

Amarok and digiKam (with small d if you notice) needs KDE Platform being installed. 

There are few things what people should know about "KDE".

1. KDE means *community*, **not software**.
2. KDE SC means software compilation (a set, package etc) what KDE release every 6 month and every month a update to it.
3. KDE SC includes few main sets of software.
[LIST]
[*]**KDE Platform**
This is the base for all. KDE libraries and main programs (konqueror belongs to this one because KHTML). You need KDE Platform to get any KDE Application to work. Somethings what belongs to this are Nepomuk, Strigi and other KDE pillars technologies.
[*]**KDE Plasma Desktop/Netbook/Mobile/Media Center**
This is the desktop. There are few different kinds
[LIST=1]
[*]Plasma Desktop (for normal desktops)
[*]Plasma Netbook (for netbooks)
[*]Plasma Mobile (for mobile devices)
[*]Plasma Media Center (for HTPC's)
[/LIST]
These draws the panels, the desktop itself, widgets, menus and includes KWin windowmanager etc. KDE Plasma is not needed if you just want to run KDE Application in GNOME or so on. KDE Plasma * is what user needs if he wants to get a desktop. But KDE Plasma * ain't a *Desktop Environment*.
[*]**KDE Applications**
These are the applications using KDE Platform (pure Qt applications are not such). Like Amarok, digiKam, Kopete, Kontact and so on. Some are part of the KDE SC (Konqueror, Kopete, Kontact) and some are just thirdparty but uses a KDE Platform (digiKam, Amarok, Konversation and so on).
[*]**KDE Development Platform**
This is the development tools what are used to develop a KDE Applications or any other software what belongs to KDE SC. You are not tied to them but they help developer a lot.  
[/LIST]

So to you if you want digiKam and Amarok, you need to install KDE Platform. And then you get digiKam and Amarok work. KDE Platform is needed as it has all what those two KDE Applications uses.

You can not get those KDE Apps without KDE platform.
And those just use diskspace for libraries etc. So if you just have disk space, everything is OK and you do not need to worry anything.

---

### Post by Dustin2128 on 2010-10-07
this^ 

KDE is a worthwhile install anyway, it makes for a solid DE.

---

