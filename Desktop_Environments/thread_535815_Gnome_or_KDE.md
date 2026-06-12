---
title: "Gnome or KDE"
date: 2007-08-26
forum: Desktop Environments
---

### Post by SpikeyMike on 2007-08-26
Hi, I am using the Gnome desktop and I installed Amarok, it does work but sometimes I get a message saying that it crashed whilst trying to do something or other. My question is, should Amarok work ok with the Gnome desktop or do I need to be using KDE? Also what exactly is the difference between Gnome and KDE? I was thinking of trying KDE out......

Spikey

---

### Post by cilynx on 2007-08-27
In theory, Amarok should work fine under Gnome.  In practice, YMMV.  Gnome vs. KDE is an ancient and never-ending debate.  It used to be that KDE was designed with the Windows transition user in mind and Gnome was designed to be powerful.  Somewhere along the lines, Gnome started becoming more user friendly and KDE started becoming more powerful.  Basically, it comes down to one simple truth for the *buntu world:

Gnome is brown.  KDE is blue.

---

### Post by aysiu on 2007-08-27
AmaroK should work fine in Gnome. Sometimes KDE applications just crash randomly. A lot of people love AmaroK, but I also have had problems with it crashing or just freezing up while indexing my music collection.

As for differences between Gnome and KDE, start here:
[http://www.psychocats.net/ubuntu/kdegnome](http://www.psychocats.net/ubuntu/kdegnome)

---

### Post by dptxp on 2007-08-27
Navigation is simple in Gnome.

You can add kde to your installation, choose Gnome OR KDE by clicking on SESSIONS at bottom left of login screen, and set one as default.

Go to terminal

sudo aptitude update
sudo aptitude install kde-core

To remove 

sudo aptitude update
sudo aptitude remove kde-core

You can use larger kubuntu-desktop instead of kde-core, I prefer the former.

Try for yourself. About 60+ MB download.

BTW, you can make Gnome BLUE and KDE Brown, you can make one look like the other.

---

### Post by misfitpierce on 2007-08-27
Exaile is alternative to using Amarok. Altho Amarok is a nice program. It should run fine as long as dependancies are installed correctly.

---

### Post by Dark Star on 2007-08-27
Yep Exaile is way better and just the replica of Amarok ```
sudo apt-get install exaile
```

---

### Post by Happy_Man on 2007-08-27
Although, the version in Feisty sucks. If you want a decent version of Exaile, compile it or get the gutsy version somehow.

---

### Post by SpikeyMike on 2007-08-27
> **Happy_Man said:**
> Although, the version in Feisty sucks. If you want a decent version of Exaile, compile it or get the gutsy version somehow.

Thanks for all your replies, I have successfully installed KDE and got it working, a couple of questions tho, do I need to log out and log in to change from Gnome to KDE or is there a shortcut to do this? also where can I find the wizard that starts up when you log into KDE for the first time? I want to change some of the settings I applied but cannot find how to start the wizard again. As for Exaile, I have installed this too but what is the gutsy version and where is it to be found?

Cheers

Spikey

---

### Post by aysiu on 2007-08-27
Yes, you need to log out and log back in again to change from Gnome to KDE.

The one exception to this would be if you're using GDM (instead of KDM) for your login manager, have *xnest* installed, and have a second user (not the one you're currently logged in as; in which case, you can Alt-F2 ```
gdmflexiserver --xnest
``` and go to a login screen *within* your current Gnome session, select KDE from the session menu, and log in as another user.

To get the wizard again, press Alt-F2 and type ```
kpersonalizer
```

---

### Post by Happy_Man on 2007-08-27
1. Yeah, you do need to log out, specify GNOME or KDE in the sessions dialog and log back in. No way around that. 

2. The wizard just changes a variety of settings in the KDE Control Center. You get at it by choosing System Settings in the main menu. Be warned, though, that there is an option to change everything from the transparency of the menus to the localization, all in one giant window. Have fun tweaking!

3. The gutsy version is in, well, the gutsy repos. :D Don't install it unless you are running Gutsy though. I think the getdeb.net version is more recent than the repo version, but if it isn't, well, then it's up to you.

EDIT: Or, instead of manually finding everything, you can use kpersonalizer like aysiu said. I didn't know that had a command..... go figure.

---

### Post by yellowband on 2007-08-27
ya i'm done with amarok for now at least.  it always freezes when indexing my music, and adding new music is a pain.  further it always screws up my ipod

---

### Post by SpikeyMike on 2007-08-27
> **Happy_Man said:**
> 
2. The wizard just changes a variety of settings in the KDE Control Center. You get at it by choosing System Settings in the main menu. Be warned, though, that there is an option to change everything from the transparency of the menus to the localization, all in one giant window. Have fun tweaking!

3. The gutsy version is in, well, the gutsy repos. :D Don't install it unless you are running Gutsy though. I think the getdeb.net version is more recent than the repo version, but if it isn't, well, then it's up to you.

EDIT: Or, instead of manually finding everything, you can use kpersonalizer like aysiu said. I didn't know that had a command..... go figure.

Ok, but I cannot find the wizard, I tried all the options in settings > control centre but couldn't find the actual wizard......

Also what is Gutsy exactly?

cheers

Spikey

---

### Post by aysiu on 2007-08-27
I already told you what the wizard is: Alt-F2 ```
kpersonalizer
```

---

### Post by SpikeyMike on 2007-08-27
> **aysiu said:**
> I already told you what the wizard is: Alt-F2 ```
kpersonalizer
```

ok, thanks :o)

---

### Post by Happy_Man on 2007-08-27
Gutsy is a shortened term for Gutsy Gibbon, the next version of Ubuntu, due out in October, but released to testers already. Like the current version is Feisty Fawn, the next version is Gutsy Gibbon. It goes in order of the alphabet, see? :D

---

### Post by kuja on 2007-08-28
Which version of amarok are you using, there have been loads of bug fixes since the version 1.4.5 that shipped with Feisty, you can get 1.4.7 from  the feisty-backports repository. Maybe it fixed your issue(s)?

---

### Post by SpikeyMike on 2007-08-30
> **kuja said:**
> Which version of amarok are you using, there have been loads of bug fixes since the version 1.4.5 that shipped with Feisty, you can get 1.4.7 from  the feisty-backports repository. Maybe it fixed your issue(s)?

Hi, I am using version 1.4.7 at the moment, is that the latest version? I have also installed Exaile which seems to work ok although Amarok is aesthetically better I think.

Also I have another question, if anyone can help, I have wipe installed and I use it in Gnome but when I start KDE it no longer appears in the menu when I right click anything. If I go to System > Preferences > Nautilus Actions Configuration it is in there but it doesn't appear in the menu. It is configured as follows:

Path:  wipe
Parameters:  -rfs %M

Spikey

---

