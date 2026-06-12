---
title: "Help me out with KDM Theme Manager on Kubuntu Hoary 5.04"
date: 2005-05-13
forum: Desktop Environments
---

### Post by Cool_dude_Prav on 2005-05-13
Hello all,

I seem to have a very horrible problem of the missing but installed pkg...  :-x  #-o 

Actually, I wanted to mod my KUbuntu using **KDM Theme Manager** and so, I tried to install it.

It asked me for the latest versions of some of the libs and I got them off the debian package site ([http://packages.debian.org](http://packages.debian.org)) and installed them properly using "dpkg -i"

Everything went fine and I also installed the KDM Theme Manager fine..

But then the problem arose... **I am unable to find the KDM Theme Manager from the Kicker Menu**... ](*,) ](*,) 
I also tried using terminal to start by typing #kdmtheme
But to no response... :(

Someone plz help me to either
:arrow: Find and use the KDM Theme Manager
OR
:arrow: Recommend a better Theme Manager that can be used on KUbuntu 5.04

Your help is very much needed!!!

Tnx in advance...

---

### Post by codejunkie on 2005-05-13
i think it shows up under the control center options under administration tab hope this helps.

---

### Post by Maestro23 on 2005-05-13
Follow these crumbs and you should find the pot of gold... \\:D/ 

Kicker...Control Center...Appearance/Themes....Theme Manager

---

### Post by Cool_dude_Prav on 2005-05-13
[QUOTE=Maestro23]Follow these crumbs and you should find the pot of gold... \\:D/ 

Kicker...Control Center...Appearance/Themes....Theme Manager[/QUOTE]
 I know the Theme Manager by default on KDE..

But this KDM Theme Manager is a third-party app supported on KDE [http://www.kde-apps.org/content/show.php?content=22120](http://www.kde-apps.org/content/show.php?content=22120)

Please re-help me

---

### Post by Maestro23 on 2005-05-13
[QUOTE=Cool_dude_Prav]I know the Theme Manager by default on KDE..

But this KDM Theme Manager is a third-party app supported on KDE [http://www.kde-apps.org/content/show.php?content=22120](http://www.kde-apps.org/content/show.php?content=22120)

Please re-help me[/QUOTE]

Ah, I saw that guy's pgm, my bad.  Did you install it just like he said and put your d/l themes where he put his?  Sorry I can't be more help, I have never used a 3rd-party theme manager pgm. The default kde theme manager suits my purposes.  Good luck though...

---

### Post by codejunkie on 2005-05-13
[QUOTE=Cool_dude_Prav]I know the Theme Manager by default on KDE..

But this KDM Theme Manager is a third-party app supported on KDE [http://www.kde-apps.org/content/show.php?content=22120](http://www.kde-apps.org/content/show.php?content=22120)

Please re-help me[/QUOTE]
instructions copied from the link you just gave here. in red ;-) 
Description:
KDM Theme manager is just what it says a theme Manager for KDM.
This control module allows you to easily add, remove and select any KDM theme you want.

The way I store what themes is directly in the kdmrc file
THEMES=/path/to/theme1/dir,/path/to/theme2/dir,etc

to install:
make -f Makefile.cvs
./configure `kde-config --prefix`
make
su -c "make install"
[COLOR=DarkRed]
To run kdmtheme simple open K Control Center and go to System Administration
There you will find KDM Theme Manager
[/COLOR]
Enjoy!

---

### Post by Cool_dude_Prav on 2005-05-13
> **codejunkie]instructions copied from the link you just gave here. in red  said:**
> 
To run kdmtheme simple open K Control Center and go to System Administration
There you will find KDM Theme Manager
[/COLOR]
Enjoy!
 Tnx a really lot
Tnx a TON!!!!!!!!!!!!!!!

u r simply the greatest!!!!!!!!!!

---

