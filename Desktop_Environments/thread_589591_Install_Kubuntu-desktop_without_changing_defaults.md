---
title: "Install Kubuntu-desktop without changing defaults"
date: 2007-10-24
forum: Desktop Environments
---

### Post by tdn on 2007-10-24
Hi

I currently use my girlfriend's laptop, because my own computer just crashed.
I use Kubuntu and she uses Ubuntu. 
I would like to install KDE and all the Kubuntu parts that I use, but I do *not* want to change all the system wide things that the kubuntu-desktop package installs, like set the default login manager to KDM in stead of GDM, or set the boot up image to Kubuntu instead of Ubuntu logo, or anything that touches her profile. I just want to be able to login to KDE (with all the Kubuntu specific parts of KDE).

How do I do this?

---

### Post by benerivo on 2007-10-24
Make a new user for you on the laptop, and install kdebase from Synaptic, then log out of ubuntu. From the login screen, you can change the session to kde and log in to kde as you. The only changes she will notice is that there are a few extra programs in the Gnome main menu such as konsole, kate, konqueror, etc, but she will never notice them and her system will be exactly the same for her.


EDIT - There wil be no Kubuntu stuff in your kde. You will have to add alll the extra programs that you are used to such as kaffeine, katapult, kontact, kpdf, etc. These extra programs will be visiible in her menu, but not affect her system or the way it works.

---

### Post by tdn on 2007-10-24
> **benerivo said:**
> Make a new user for you on the laptop, and install kdebase from Synaptic, then log out of ubuntu. From the login screen, you can change the session to kde and log in to kde as you. The only changes she will notice is that there are a few extra programs in the Gnome main menu such as konsole, kate, konqueror, etc, but she will never notice them and her system will be exactly the same for her.


EDIT - There wil be no Kubuntu stuff in your kde. You will have to add alll the extra programs that you are used to such as kaffeine, katapult, kontact, kpdf, etc. These extra programs will be visiible in her menu, but not affect her system or the way it works.

Is there a meta package I can install to get all of those apps?
What about the Kubuntu specific settings for KDE? Do I get those?

---

### Post by tdn on 2007-10-24
> **tdn said:**
> Is there a meta package I can install to get all of those apps?
What about the Kubuntu specific settings for KDE? Do I get those?

It seems that kdebase depends on something that needs kdm, but I would not want to have kdm as the login manager.

```

~ $ aptitude show kdebase
Package: kdebase
State: not installed
Version: 4:3.5.8-0ubuntu2
Priority: frivillig
Section: kde
Maintainer: Jonathan Riddell <jriddell@ubuntu.com>
Uncompressed Size: 102k
Depends: kappfinder (>= 4:3.5.8-0ubuntu2), kate (>= 4:3.5.8-0ubuntu2), kcontrol
         (>= 4:3.5.8-0ubuntu2), kdebase-bin (>= 4:3.5.8-0ubuntu2), kdebase-data
         (>= 4:3.5.8-0ubuntu2), kdebase-kio-plugins (>= 4:3.5.8-0ubuntu2),
         kdepasswd (>= 4:3.5.8-0ubuntu2), kdeprint (>= 4:3.5.8-0ubuntu2),
         kdesktop (>= 4:3.5.8-0ubuntu2), kfind (>= 4:3.5.8-0ubuntu2),
         khelpcenter (>= 4:3.5.8-0ubuntu2), kicker (>= 4:3.5.8-0ubuntu2),
         klipper (>= 4:3.5.8-0ubuntu2), kmenuedit (>= 4:3.5.8-0ubuntu2),
         konqueror-nsplugins (>= 4:3.5.8-0ubuntu2), konqueror (>=
         4:3.5.8-0ubuntu2), konsole (>= 4:3.5.8-0ubuntu2), kpager (>=
         4:3.5.8-0ubuntu2), kpersonalizer (>= 4:3.5.8-0ubuntu2), ksmserver (>=
         4:3.5.8-0ubuntu2), ksplash (>= 4:3.5.8-0ubuntu2), ksysguard (>=
         4:3.5.8-0ubuntu2), ktip (>= 4:3.5.8-0ubuntu2), kwin (>=
         4:3.5.8-0ubuntu2), libkonq4 (>= 4:3.5.8-0ubuntu2), hal | kfreebsd-gnu |
         hurd
Recommends: kdm (>= 4:3.5.8-0ubuntu2)
Suggests: kdebase-doc-html (>= 4:3.5.8-0ubuntu2)
Description: base components from the official KDE release
 KDE (the K Desktop Environment) is a powerful Open Source graphical desktop
 environment for Unix workstations. It combines ease of use, contemporary
 functionality, and outstanding graphical design with the technological
 superiority of the Unix operating system. 
 
 This metapackage includes the nucleus of KDE, namely the minimal package set
 necessary to run KDE as a desktop environment. This includes the window
 manager, taskbar, control center, a text editor, file manager, web browser, X
 terminal emulator, and many other programs and components.

```

---

### Post by benerivo on 2007-10-24
Don't take kdm. I know if you install kdebase from Synaptic it won't include kdm. To get extra packages that are included with Kubuntu, then search for kde in Synaptic. It will have several metapackages that cover different types of apps. They're called things like kde-artwork, kde-multimedia, kde-graphics, kde-toys. This will get you pretty much everything that kubuntu comes with. There is n't a single kubuntu package that gives you just the kubuntu apps. One way to do it may be to install the full kubuntu package then remove kdm. I would guess that should give you all the apps without changing the system, but it will ruin your girlfriend's main menu, and is not worth the risk of other potential changes.

Personally i would kust do kde base then maybe a couple of the kde meta packages.


EDIT - I've just remembered that there is a package that is called something like kubuntu-settings. It doesn't give you the apps but does change some settings to match kubuntu. For example, it makes dophin the default file manager (you will need to install dolphin separately), and installs kubuntu's artwork.

---

### Post by tdn on 2007-11-08
I have installed kdebase and kde-artwork and such. But I still have the problem that when I open folders from Kicker they are opened in Konqueror. I want to ONLY use Dolphin for file browsing. I have set Dolphin to the default file browser by setting file associations on inodes.

Here are some other problems I am experiencing:

Also for some reason alt+space does not give me Katapult even though it is installed.

I also have problems adjusting sound volumes.

---

