---
title: "install KDE?"
date: 2006-07-12
forum: Desktop Environments
---

### Post by shortbus on 2006-07-12
I am currently using ubuntu with Gnome. I am wanting to also install KDE.
I did 'sudo apt-get install kdebase' and got the following message:
shortbus@shortbus-laptop:~$ sudo apt-get install kdebase
Password:
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  kdebase: Depends: kappfinder (>= 4:3.4.3-0ubuntu7) but it is not going to be installed
           Depends: kate (>= 4:3.4.3-0ubuntu7) but it is not going to be installed
           Depends: kcontrol (>= 4:3.4.3-0ubuntu7) but it is not going to be installed
           Depends: kdebase-bin (>= 4:3.4.3-0ubuntu7) but it is not going to be installed
           Depends: kdebase-kio-plugins (>= 4:3.4.3-0ubuntu7) but it is not going to be installed
           Depends: kdepasswd (>= 4:3.4.3-0ubuntu7) but it is not going to be installed
           Depends: kdeprint (>= 4:3.4.3-0ubuntu7) but it is not going to be installed
           Depends: kdesktop (>= 4:3.4.3-0ubuntu7) but it is not going to be installed
           Depends: kfind (>= 4:3.4.3-0ubuntu7) but it is not going to be installed
           Depends: khelpcenter (>= 4:3.4.3-0ubuntu7) but it is not going to be installed
           Depends: kicker (>= 4:3.4.3-0ubuntu7) but it is not going to be installed
           Depends: klipper (>= 4:3.4.3-0ubuntu7) but it is not going to be installed
           Depends: kmenuedit (>= 4:3.4.3-0ubuntu7) but it is not going to be installed
           Depends: konqueror-nsplugins (>= 4:3.4.3-0ubuntu7) but it is not going to be installed
           Depends: konqueror (>= 4:3.4.3-0ubuntu7) but it is not going to be installed
           Depends: konsole (>= 4:3.4.3-0ubuntu7) but it is not going to be installed
           Depends: kpager (>= 4:3.4.3-0ubuntu7) but it is not going to be installed
           Depends: kpersonalizer (>= 4:3.4.3-0ubuntu7) but it is not going to be installed
           Depends: ksmserver (>= 4:3.4.3-0ubuntu7) but it is not going to be installed
           Depends: ksplash (>= 4:3.4.3-0ubuntu7) but it is not going to be installed
           Depends: ksysguard (>= 4:3.4.3-0ubuntu7) but it is not going to be installed
           Depends: ktip (>= 4:3.4.3-0ubuntu7) but it is not going to be installed
           Depends: kwin (>= 4:3.4.3-0ubuntu7) but it is not going to be installed
           Depends: libkonq4 (>= 4:3.4.3-0ubuntu7) but it is not going to be installed
E: Broken packages
shortbus@shortbus-laptop:~$

I am a bit stuck as to what I need to do now.]

---

### Post by mogelhead on 2006-07-12
I think the correct way is to install kubuntu-desktop.

See ["I already have Ubuntu installed, how can I get Kubuntu?"]("http://www.kubuntu.org/faq.php#installfromubuntu") on the kubuntu site.

---

### Post by Viper666 on 2006-07-12
maybe u don't have all repository's enabled?

---

### Post by shortbus on 2006-07-12
n00b question then... how do i enable all the repository's?

---

### Post by Viper666 on 2006-07-12
try this [http://www.ubuntuforums.org/showthread.php?t=185758](http://www.ubuntuforums.org/showthread.php?t=185758)

---

### Post by daniel of sarnia on 2006-07-12
kubuntu-desktop is in the defalt repos anyways

---

### Post by lurchi on 2006-07-12
> **shortbus said:**
> n00b question then... how do i enable all the repository's?

remove the comment-signs in /etc/apt/sources.list

---

### Post by daniel of sarnia on 2006-07-12
however for kubuntu-desktop it dose not matter, everthing is in the main repos anyways. All he has to do is sudo apt-get install kubuntu-desktop

---

### Post by Viper666 on 2006-07-12
> **daniel of sarnia said:**
> kubuntu-desktop is in the defalt repos anyways

It is but the other files which it depends on are not. :)

---

### Post by shortbus on 2006-07-12
> **daniel of sarnia said:**
> sudo apt-get install kubuntu-desktop

this is what i get when I just do that:
shortbus@shortbus-laptop:~$ sudo apt-get install kubuntu-desktop
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  kubuntu-desktop: Depends: adept but it is not going to be installed
                   Depends: akode but it is not going to be installed
                   Depends: akregator but it is not going to be installed
                   Depends: amarok but it is not going to be installed
                   Depends: ark but it is not going to be installed
                   Depends: cupsys-driver-gimpprint but it is not going to be installed
                   Depends: gtk2-engines-gtk-qt but it is not going to be installed
                   Depends: gwenview but it is not going to be installed
                   Depends: hplip-base but it is not going to be installed
                   Depends: ivman but it is not going to be installed
                   Depends: k3b but it is not going to be installed
                   Depends: kaddressbook but it is not going to be installed
                   Depends: kaffeine-gstreamer but it is not going to be installed
                   Depends: kamera but it is not going to be installed
                   Depends: karm but it is not going to be installed
                   Depends: katapult but it is not going to be installed
                   Depends: kate but it is not going to be installed
                   Depends: kaudiocreator but it is not going to be installed
                   Depends: kcontrol but it is not going to be installed
                   Depends: kcron but it is not going to be installed
                   Depends: kde-guidance but it is not going to be installed
                   Depends: kde-systemsettings but it is not going to be installed
                   Depends: kdeadmin-kfile-plugins but it is not going to be installed
                   Depends: kdebase-kio-plugins but it is not going to be installed
                   Depends: kdebluetooth but it is not going to be installed
                   Depends: kdegraphics-kfile-plugins but it is not going to be installed
                   Depends: kdemultimedia-kappfinder-data but it is not going to be installed
                   Depends: kdemultimedia-kfile-plugins but it is not going to be installed
                   Depends: kdemultimedia-kio-plugins but it is not going to be installed
                   Depends: kdenetwork-filesharing but it is not going to be installed
                   Depends: kdenetwork-kfile-plugins but it is not going to be installed
                   Depends: kdepasswd but it is not going to be installed
                   Depends: kdepim-kio-plugins but it is not going to be installed
                   Depends: kdepim-wizards but it is not going to be installed
                   Depends: kdeprint but it is not going to be installed
                   Depends: kdesktop but it is not going to be installed
                   Depends: kdm but it is not going to be installed
                   Depends: kfind but it is not going to be installed
                   Depends: kghostview but it is not going to be installed
                   Depends: khelpcenter but it is not going to be installed
                   Depends: kicker but it is not going to be installed
                   Depends: kio-apt but it is not going to be installed
                   Depends: kio-locate but it is not going to be installed
                   Depends: klaptopdaemon but it is not going to be installed
                   Depends: klipper but it is not going to be installed
                   Depends: kmail but it is not going to be installed
                   Depends: kmenuedit but it is not going to be installed
                   Depends: kmilo but it is not going to be installed
                   Depends: kmix but it is not going to be installed
                   Depends: knetworkconf but it is not going to be installed
                   Depends: knotes but it is not going to be installed
                   Depends: konq-plugins but it is not going to be installed
                   Depends: konqueror but it is not going to be installed
                   Depends: konqueror-nsplugins but it is not going to be installed
                   Depends: konserve but it is not going to be installed
                   Depends: konsole but it is not going to be installed
                   Depends: kontact but it is not going to be installed
                   Depends: konversation but it is not going to be installed
                   Depends: kooka but it is not going to be installed
                   Depends: kopete but it is not going to be installed
                   Depends: korganizer but it is not going to be installed
                   Depends: kpdf but it is not going to be installed
                   Depends: kpf but it is not going to be installed
                   Depends: kppp but it is not going to be installed
                   Depends: krdc but it is not going to be installed
                   Depends: krfb but it is not going to be installed
                   Depends: krita but it is not going to be installed
                   Depends: kscd but it is not going to be installed
                   Depends: kscreensaver but it is not going to be installed
                   Depends: ksmserver but it is not going to be installed
                   Depends: ksnapshot but it is not going to be installed
                   Depends: ksplash but it is not going to be installed
                   Depends: ksvg but it is not going to be installed
                   Depends: ksysguard but it is not going to be installed
                   Depends: ksystemlog but it is not going to be installed
                   Depends: kubuntu-default-settings but it is not going to be installed
                   Depends: kubuntu-docs but it is not going to be installed
                   Depends: kubuntu-konqueror-shortcuts but it is not going to be installed
                   Depends: kuser but it is not going to be installed
                   Depends: kwalletmanager but it is not going to be installed
                   Depends: kwifimanager but it is not going to be installed
                   Depends: kwin but it is not going to be installed
                   Depends: openoffice.org2-kde but it is not going to be installed
E: Broken packages
shortbus@shortbus-laptop:~$
](*,)

---

### Post by Viper666 on 2006-07-12
copy the contents of your /etc/apt/sources.list here

---

### Post by daniel of sarnia on 2006-07-12
I'm not too sure what to do about that, as every time I've install ubuntu and the apt-get kubuntu-desktop afterwords everything just worked.

Maybe try, sudo apt-get remove kdebase and sudo apt-get remove kubuntu-desktop and finaly sudo apt-get install kubuntu-desktop

If that dose not help then I'm not sure, you'll want to wate till someone with more ubuntu experience sees this to help out.

---

### Post by daniel of sarnia on 2006-07-12
"copy the contents of your /etc/apt/sources.list here"

that may help us too

---

### Post by shortbus on 2006-07-12
#deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted


deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
 deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe
 deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe

 deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse
 deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
# deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

 deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
 deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

 deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security multiverse
 deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security multiverse

## PLF repositories, contains litigious packages, see [http://wiki.ubuntu-fr.org/doc/plf](http://wiki.ubuntu-fr.org/doc/plf)
deb [http://antesis.freecontrib.org/mirrors/ubuntu/plf/](http://antesis.freecontrib.org/mirrors/ubuntu/plf/) breezy free non-free
deb-src [http://antesis.freecontrib.org/mirrors/ubuntu/plf/](http://antesis.freecontrib.org/mirrors/ubuntu/plf/) breezy free non-free

## Freecontrib, funny packages by the Ubuntu PLF Team
deb [http://antesis.freecontrib.org/mirrors/ubuntu/freecontrib/](http://antesis.freecontrib.org/mirrors/ubuntu/freecontrib/) breezy free non-free
deb-src [http://antesis.freecontrib.org/mirrors/ubuntu/freecontrib/](http://antesis.freecontrib.org/mirrors/ubuntu/freecontrib/) breezy free non-free

---

### Post by Viper666 on 2006-07-12
delete any ## infront of deb's. And try sudo apt-get update and after that

sudo apt-get kubuntu-desktop if it still gives an error... i don't have a clue.

Maybe try upgrading to Dapper would help?

---

### Post by shortbus on 2006-07-12
I'll give it a shot, is there any other way aside from VI to edit that file? I hate VI with a passion.

---

### Post by Twinxor on 2006-07-12
> **shortbus said:**
> I'll give it a shot, is there any other way aside from VI to edit that file? I hate VI with a passion.

nano is pretty simple to use.

---

### Post by Twinxor on 2006-07-12
> **Viper666 said:**
> delete any ## infront of deb's. And try sudo apt-get update and after that

sudo apt-get kubuntu-desktop if it still gives an error... i don't have a clue.

Maybe try upgrading to Dapper would help?

Did you look at his file? He already has universe enabled. Enabling others like backports won't help.

---

### Post by shortbus on 2006-07-12
> **daniel of sarnia said:**
> I'm not too sure what to do about that, as every time I've install ubuntu and the apt-get kubuntu-desktop afterwords everything just worked.

Maybe try, sudo apt-get remove kdebase and sudo apt-get remove kubuntu-desktop and finaly sudo apt-get install kubuntu-desktop

If that dose not help then I'm not sure, you'll want to wate till someone with more ubuntu experience sees this to help out.

well, they never got installed so I can't remove them.

---

### Post by Viper666 on 2006-07-12
or... u could download Kubuntu and that's it :mrgreen:

---

### Post by shortbus on 2006-07-12
have a copy of Kubuntu, but i am more of a fan of Gnome, but there are something for KDE i want to use.

---

