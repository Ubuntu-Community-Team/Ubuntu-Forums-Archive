---
title: "Help me out with this - using KUbuntu 5.04"
date: 2005-05-12
forum: Desktop Environments
---

### Post by Cool_dude_Prav on 2005-05-12
Hello all,

I seem to have a very horrible problem of the missing but installed pkg...  :-x  #-o 

Actually, I wanted to mod my KUbuntu using **KDM Theme Manager** and so, I tried to install it.

It asked me for the latest versions of some of the libs and I got them off the debian package site ([http://packages.debian.org](http://packages.debian.org)) and installed them properly using "dpkg -i"

Everything went fine and I also installed the KDM Theme Manager fine..

But then the problem arose... **I am unable to find the KDM Theme Manager from the Kicker Menu**... (*,) ](*,) 
I also tried using terminal to start by typing #kdmtheme
But to no response... :(

Someone plz help me to either
:arrow: Find and use the KDM Theme Manager
OR
:arrow: Recommend a better Theme Manager that can be used on KUbuntu 5.04

Your help is very much needed!!!

Tnx in advance...

---

### Post by tread on 2005-05-12
Warning: my post doesn't help much :) 

I read somewhere that it is unwise to mix ubuntu and debian repositories/packages .. have you tried enabling the other repositories in your sources.list file? There are quite a few listed on the unofficial ubuntu guide.

---

### Post by Cool_dude_Prav on 2005-05-12
[QUOTE=tread]Warning: my post doesn't help much :) 

I read somewhere that it is unwise to mix ubuntu and debian repositories/packages .. have you tried enabling the other repositories in your sources.list file? There are quite a few listed on the unofficial ubuntu guide.[/QUOTE]
 Seems you have misunderstood me...

What I have mentioned is that I have perfectly installed the KDM Theme Manager, but I am unable to find it in order to open and use it.. :(

And reg: the info that Ubuntu and Debian don't mix... I will try not to do it in future :)

Anyone else, plz help me!!!

---

### Post by az on 2005-05-12
The point is that if you use packages from debian, they may not work and they may bork you package system.


Use only ubuntu repositories and use synaptic or apt to install stuff.  Stay away from dpkg -i unless you really need to.

---

### Post by Cool_dude_Prav on 2005-05-12
[QUOTE=azz]The point is that if you use packages from debian, they may not work and they may bork you package system.


Use only ubuntu repositories and use synaptic or apt to install stuff.  Stay away from dpkg -i unless you really need to.[/QUOTE]
 But the GAIM 1.2.1 I installed was from those pkgs as Ubuntu was having out0dated packages!!! :(

Then, is there a way to add some repositories thro' which I can install KDM Theme Manager???

---

### Post by Cool_dude_Prav on 2005-05-12
Someone plz help me...

Or else atleast recommend me a better Theme Manager!!!

---

### Post by derrick1985 on 2005-05-12
I'm going to suggest something completely radical....


UNINSTALL the packages you have, and read through [http://www.ubuntuguide.org](http://www.ubuntuguide.org) on enabling the right repositories for your ubuntu system, andt ry getting them from there.

All the packages on the ubuntu repositories (universe/multiverse/backports) will work and install properly with your ubuntu system.

Gaim is outdated, yes, If you enable the backports repositories ([http://backports.ubuntuforums.org](http://backports.ubuntuforums.org)) you will not get that problem.

[http://www.ubuntuguide.org/#repositories](http://www.ubuntuguide.org/#repositories)

---

### Post by wvslkr on 2005-05-13
I am not familiar with program;but "If" it actually installed correctly and is usable I would guess it is in /usr/bin. Check and look at command syntax.  Still
safer to use repositories suggested.     :)

---

### Post by bored2k on 2005-05-13
I just downloaded it through Pacote's debian website. The minute it asked me for unmet dependencies from ubuntu repositories, I knew I would get in trouble. This -might- have worked, but it will cripple your future apt-get upgrades *amigo*. Don't.

---

### Post by Cool_dude_Prav on 2005-05-13
[QUOTE=bored2k]I just downloaded it through Pacote's debian website. The minute it asked me for unmet dependencies from ubuntu repositories, I knew I would get in trouble. This -might- have worked, but it will cripple your future apt-get upgrades *amigo*. Don't.[/QUOTE]
 Then how the heck am I supposed to mod my Linux KDE themes?

Even KDE-Look has got only 8 themes :(

---

### Post by bored2k on 2005-05-13
[QUOTE=Cool_dude_Prav]Then how the heck am I supposed to mod my Linux KDE themes?

Even KDE-Look has got only 8 themes :([/QUOTE]
 Get your hands dirty through the terminal window :D

For comodity, paste your themes in
/usr/share/apps/kdm/themes

Then edit your
/etc/kde3/kdm/kdmrc
so it loads THAT theme.

Maybe i'll make a howto on this and more topics once I get back from school..

---

### Post by Cool_dude_Prav on 2005-05-13
[QUOTE=bored2k]Get your hands dirty through the terminal window :D

For comodity, paste your themes in
/usr/share/apps/kdm/themes

Then edit your
/etc/kde3/kdm/kdmrc
so it loads THAT theme.

Maybe i'll make a howto on this and more topics once I get back from school..[/QUOTE]
 Well.. I am surely waiting for that HOWTO...

Tnx in advance..

---

### Post by bored2k on 2005-05-13
[QUOTE=Cool_dude_Prav]Well.. I am surely waiting for that HOWTO...

Tnx in advance..[/QUOTE]
 I'll get started then ..

---

