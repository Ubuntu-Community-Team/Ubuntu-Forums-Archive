---
title: "Cant upgrade from KDE 3.4.2 to 3.5.x"
date: 2006-02-03
forum: Desktop Environments
---

### Post by chetanthaker on 2006-02-03
Hey guys

I'm a newbie to Kubuntu and love the KDE desktop and have got v3.4 installed (found out thru kControl) and I'd like to upgrade to v3.5.x

I added the repository 

sudo apt-key add kubuntu-packages-jriddell-key.gpg   
wget [http://people.ubuntu.com/~jriddell/kubuntu-packages-jriddell-key.gpg](http://people.ubuntu.com/~jriddell/kubuntu-packages-jriddell-key.gpg)    

and I get a OK in the end

After that when i do a 

sudo apt-get update
sodu apt-get upgrade
sudo apt-get upgrade-dist, it says

> ceetee@ceeteebox:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree... Done
Calculating upgrade... Done
The following packages have been kept back:
  akregator ark artsbuilder kaddressbook kamera kappfinder karm kate kaudiocreator kcontrol kcron kdeadmin-kfile-plugins
  kdebase-bin kdebase-kio-plugins kdegraphics-kfile-plugins kdelibs-bin kdelibs4c2 kdemultimedia-kfile-plugins
  kdemultimedia-kio-plugins kdenetwork-filesharing kdenetwork-kfile-plugins kdepasswd kdepim-kio-plugins kdepim-wizards
  kdeprint kdesktop kdm kfind kghostview khelpcenter kicker klaptopdaemon klipper kmenuedit kmilo kmix knetworkconf
  knotes konq-plugins konqueror konqueror-nsplugins konsole kontact kooka kopete korganizer kpdf kpf kppp krdc krfb kscd
  kscreensaver ksmserver ksnapshot ksplash ksvg kuser kwalletmanager kwifimanager kwin libkcddb1 libkonq4
  libkpimexchange1 libkpimidentities1 libkscan1 libksieve0 libktnef1
0 upgraded, 0 newly installed, 0 to remove and 68 not upgraded.


I restart the PC but still the old version is retained

Is there anyone who can help me out here ??

Thanx and Cheers

CeeTee

---

### Post by JimmyJazz on 2006-02-03
sudo apt-get update
then...
sudo apt-get upgrade

its not a distro upgrade and that is what you where doing.

---

### Post by MartinG on 2006-02-03
[QUOTE=chetanthaker]I added the repository 

sudo apt-key add kubuntu-packages-jriddell-key.gpg   
wget [http://people.ubuntu.com/~jriddell/kubuntu-packages-jriddell-key.gpg](http://people.ubuntu.com/~jriddell/kubuntu-packages-jriddell-key.gpg)    

and I get a OK in the end

[/QUOTE]Not quite clear. The command "sudo apt-key add" doesn't add a repository, only imports the key; did you add the repository **as well** (edit /etc/apt/sources.list, or do it in Synaptic)?  What does your sources.list look like now?

You don't need to upgrade *and* to dist-upgrade.  The difference (roughly) is that dist-upgrade will remove or add dependencies, whereas upgrade will not add or remove packages, only upgrade existing ones.

---

### Post by chetanthaker on 2006-02-03
Will PM you the sources.list file in a couple of hours -- Im not at home.. Im in college

Please do advice once you get the file from me 

CeeTee

---

### Post by NeoChaosX on 2006-02-03
What you forgot to do is add this line to /etc/apt/sources.list:
```
deb http://kubuntu.org/packages/kde351 breezy main
```

Add that line to that file, then update and (dist-)upgrade again.

---

### Post by chetanthaker on 2006-02-03
Ok, I got it working

Just added these in the /etc/apt/sources.list file

deb [http://pkg-kde.alioth.debian.org/kde-3.5-rc1](http://pkg-kde.alioth.debian.org/kde-3.5-rc1) ./
deb-src [http://pkg-kde.alioth.debian.org/kde-3.5-rc1](http://pkg-kde.alioth.debian.org/kde-3.5-rc1) ./

and upgraded it -- works fine :)


Thanx y'all

P E A C E !!

CeeTee

---

### Post by stimpack on 2006-02-03
For future reference, follow the instrucutions at kubuntu.org.

You should have used; deb [http://kubuntu.org/packages/kde351](http://kubuntu.org/packages/kde351) breezy main

AFAIK and I could be wrong but I beleive Kubuntu is not garenteed to be binary compatable with debian. But as it works thats cool, Id leave it be now.

---

