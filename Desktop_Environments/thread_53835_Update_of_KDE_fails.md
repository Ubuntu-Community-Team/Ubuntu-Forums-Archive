---
title: "Update of KDE fails"
date: 2005-08-02
forum: Desktop Environments
---

### Post by ghostryder on 2005-08-02
Hi,

I'm trying to update KDE to version 3.4.2 but it always yields to:

$ sudo apt-get install kdebase
Reading package lists... Done
Building dependency tree... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  kdebase: Depends: kappfinder (>= 4:3.4.2-0ubuntu0hoary1) but 4:3.4.0-0ubuntu18 is to be installed
           Depends: kdebase-kio-plugins (>= 4:3.4.2-0ubuntu0hoary1) but 4:3.4.0-0ubuntu18 is to be installed
           Depends: kdepasswd (>= 4:3.4.2-0ubuntu0hoary1) but 4:3.4.0-0ubuntu18 is to be installed
           Depends: kdeprint (>= 4:3.4.2-0ubuntu0hoary1) but 4:3.4.0-0ubuntu18 is to be installed
           Depends: kdesktop (>= 4:3.4.2-0ubuntu0hoary1) but 4:3.4.0-0ubuntu18 is to be installed
           Depends: kfind (>= 4:3.4.2-0ubuntu0hoary1) but 4:3.4.0-0ubuntu18 is to be installed
           Depends: khelpcenter (>= 4:3.4.2-0ubuntu0hoary1) but 4:3.4.0-0ubuntu18 is to be installed
           Depends: klipper (>= 4:3.4.2-0ubuntu0hoary1) but 4:3.4.0-0ubuntu18 is to be installed
           Depends: kmenuedit (>= 4:3.4.2-0ubuntu0hoary1) but 4:3.4.0-0ubuntu18 is to be installed
           Depends: konqueror-nsplugins (>= 4:3.4.2-0ubuntu0hoary1) but 4:3.4.0-0ubuntu18 is to be installed
           Depends: konqueror (>= 4:3.4.2-0ubuntu0hoary1) but 4:3.4.0-0ubuntu18 is to be installed
           Depends: konsole (>= 4:3.4.2-0ubuntu0hoary1) but 4:3.4.0-0ubuntu18 is to be installed
           Depends: kpager (>= 4:3.4.2-0ubuntu0hoary1) but 4:3.4.0-0ubuntu18 is to be installed
           Depends: kpersonalizer (>= 4:3.4.2-0ubuntu0hoary1) but 4:3.4.0-0ubuntu18 is to be installed
           Depends: ksmserver (>= 4:3.4.2-0ubuntu0hoary1) but 4:3.4.0-0ubuntu18 is to be installed
           Depends: ksplash (>= 4:3.4.2-0ubuntu0hoary1) but 4:3.4.0-0ubuntu18 is to be installed
           Depends: ksysguard (>= 4:3.4.2-0ubuntu0hoary1) but 4:3.4.0-0ubuntu18 is to be installed
           Depends: ktip (>= 4:3.4.2-0ubuntu0hoary1) but it is not going to be installed
  kdelibs: Depends: kdelibs-data (>= 4:3.4.2-0ubuntu0hoary1) but 4:3.4.0-0ubuntu3 is to be installed
  kdevelop3-data: Depends: kdevelop3 (= 4:3.2.0-0ubuntu1) but 4:3.2.2-0ubuntu0hoary1 is to be installed

I already tried to use option -f but that didn't help. Same problem with nvidia-driver. 

thanks, g.

---

### Post by SGC on 2005-08-02
Try:
sudo apt-get update
sudo apt-get upgrade

If that doesn't works, then please post the contents of your /etc/apt/sources.list file here.

Also what version of kde are you using now?

---

### Post by ghostryder on 2005-08-02
I have already tried these commands. They lead to an error. My sources.list looks liks as follows:

eb cdrom:[Kubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted

## Uncomment the following two lines to fetch updated software from the network
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse

## Backports
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted

#KDE-3.4.2
deb [http://kubuntu.org/hoary-kde342](http://kubuntu.org/hoary-kde342) hoary-updates main

I'm working with KDE 3.4.0 at the moment. It's the one from the base installation.

thanks, g.

---

### Post by arjaybe on 2005-08-02
[QUOTE=ghostryder]I have already tried these commands. They lead to an error. My sources.list looks liks as follows:

eb cdrom:[Kubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted

## Uncomment the following two lines to fetch updated software from the network
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse

## Backports
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted

#KDE-3.4.2
deb [http://kubuntu.org/hoary-kde342](http://kubuntu.org/hoary-kde342) hoary-updates main

I'm working with KDE 3.4.0 at the moment. It's the one from the base installation.

thanks, g.[/QUOTE]
 That looks a lot like my sources.list.  Yesterday I did an update and dist-upgrade after replacing the KDE 3.4.1 source with the 3.4.2 one.  A few packages were upgraded while over 100 were held back.  That's not unusual and I'm prepared to wait until APT is ready to complete the upgrade.  I've learned from experience that waiting for APT is better than trying to force things manually, but you might have a different philosophy.

What error did you get when you ran upgrade?

---

### Post by ghostryder on 2005-08-02
$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  kdelibs: Depends: kdelibs-data (>= 4:3.4.2-0ubuntu0hoary1) but 4:3.4.0-0ubuntu3 is installed
  kdevelop3-data: Depends: kdevelop3 (= 4:3.2.0-0ubuntu1) but 4:3.2.2-0ubuntu0hoary1 is installed
E: Unmet dependencies. Try using -f.

That's all. So you think it's better to wait?

---

### Post by arjaybe on 2005-08-02
Actually I just remembered that I had several kdelibs packages pinned in /etc/apt/preferences because they were having problems earlier.  I unpinned them and re-ran apt-get dist-upgrade this morning and it downloaded and installed/upgraded 139 packages without a hitch.  It seems to be working fine.

Check and see if you have a /etc/apt/preferences file.

---

### Post by skyboy on 2005-08-03
try adding this line
deb-src [http://kubuntu.org/hoary-kde342](http://kubuntu.org/hoary-kde342) hoary-updates main

then 
sudo apt-get update
sudo apt-get upgrade
sudo apt-get -f install (in case it bring errors)

---

### Post by Roptaty on 2005-08-03
ghostryder, do you have 
```
 
APT::Default-Release

``` set in apt.conf?

If you have it set to hoary, you may add 
```

Package: *
Pin: origin kubuntu.org
Pin-Priority: 991

```
to your /etc/apt/preferences file.

---

### Post by kheno on 2005-08-07
I have the same problem when i try to install kde on ubuntu hoary 5.04
i tried :
sudo apt-get update
sudo apt-get upgrade
sudo apt-get -f install
and nothing works for me, this is my source.list file:
```
deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted


deb [http://br.archive.ubuntu.com/ubuntu](http://br.archive.ubuntu.com/ubuntu) hoary main restricted
deb-src [http://br.archive.ubuntu.com/ubuntu](http://br.archive.ubuntu.com/ubuntu) hoary main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb [http://kubuntu.org/hoary-kde342](http://kubuntu.org/hoary-kde342) hoary-updates main
deb-src [http://kubuntu.org/hoary-kde342](http://kubuntu.org/hoary-kde342) hoary-updates main

## Uncomment the following two lines to fetch updated software from the network
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse

## Backports
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted
```
somebody can help me ?
thanks

---

### Post by Gezzer on 2005-08-07
[QUOTE=][/QUOTE]
 here is my list ...
notice the / after kde342



deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hoary universe 
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hoary universe 

deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hoary-security main restricted 
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hoary-security main restricted 

deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hoary-security universe 
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hoary-security universe 

#### backports
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted 
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted 
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras-staging main universe multiverse restricted 
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports-staging main universe multiverse restricted 

##Kubuntu
deb [http://kubuntu.org/hoary-kde342/](http://kubuntu.org/hoary-kde342/) hoary-updates main 
deb-src [http://kubuntu.org/hoary-kde342/](http://kubuntu.org/hoary-kde342/) hoary-updates main

---

### Post by kheno on 2005-08-07
didnt worked for me :/

---

### Post by Gezzer on 2005-08-07
[QUOTE=][/QUOTE]
try in a konsole
kdesu kate

when kate is open
browse to the /apt/sources-list file

then do the editing for the list, save changes

in the konsole
sudo apt-get update

then open synaptic and try the updates ...

---

### Post by kheno on 2005-08-07
Sorry for didnt saying this: i dont have kde yet, so i am with gnome, and i cant install kde ;/

see ya

---

### Post by kheno on 2005-08-09
nobody knows? plz help mee

---

### Post by Drain on 2005-08-09
[QUOTE=kheno]nobody knows? plz help mee[/QUOTE]

First, kheno, nobody knows because you don't seem to be giving us much information about what you've tried, what you've accomplised, and what error messages you are getting. [This guide](http://www.catb.org/~esr/faqs/smart-questions.html) can be helpful in telling you what to ask us about.

Second, you should be able to install KDE with te repositories you have. (According to the [Kubuntu Documentation](http://www.kubuntu.org/documentation.php), the packages are in "hoary universe") And I may be completely underestimating you or misunderstanding you, but I have no idea - you did try to install KDE by typing:

$ sudo apt-get update
$ sudo apt-get install kubuntu-desktop

---

### Post by kheno on 2005-08-09
My problem is the same of who created this topic,the errors mensages, everything exactly the same, the difference between us is only one: he has kde installed and i am trying to install it. I tried everything:
```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install kde 
sudo apt-get install kubuntu-desktop
sudo apt-get -f install
```
I can post the error mensages, but it is in portuguese, but i will try to translate it:
```
Reading package lists... Done
Building dependency tree... Done
   Some packages could not have been installed. This can mean that you it requested an impossible situation or if you are using the unstable distribution, that some required packages had not been created or had been still taken off of the Incoming.
   Since you it requested an only operation is well probable that the package is simply not instalável and a story of error on these packages must be sent. The information to follow can help to decide the situation: The packages to follow have failed to meet dependences: 
kubuntu-desktop: 
Depends: k3b but does not go to be installed 
Depends: kaffeine but does not go to be installed 
Depends: kdebase but does not go to be installed 
Depends: kdegraphics but does not go to be installed 
Depends: kdemultimedia but does not go to be installed 
Depends: knetworkconf but does not go to be installed 
Depends: konq-plugins but does not go to be installed 
Depends: to kscreensaver but does not go to be installed 
Depends: kynaptic but does not go to be installed 
E: Broken packages
```
thats it.. and when i said "nobody knows?" i didnt mean that people in this forum are noobs etc etc sorry, it wasnt my intention 

see ya and thanks

---

### Post by Gezzer on 2005-08-09
try downloading the Kubuntu ISO
burn that to disc then install KDE it may be an easier option then updating

try here for the download ...
[http://tinyurl.com/dkmxy](http://tinyurl.com/dkmxy)

---

### Post by Roptaty on 2005-08-09
kheno: Please post the output of the command: apt-cache policy

---

### Post by kheno on 2005-08-10
Arquivos de Pacotes :
 100 /var/lib/dpkg/status
     release a=now
 500 [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/restricted Packages
     origin ubuntu-backports.mirrormax.net
 500 [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/multiverse Packages
     origin ubuntu-backports.mirrormax.net
 500 [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/universe Packages
     origin ubuntu-backports.mirrormax.net
 500 [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/main Packages
     origin ubuntu-backports.mirrormax.net
 500 [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/restricted Packages
     origin ubuntu-backports.mirrormax.net
 500 [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/multiverse Packages
     origin ubuntu-backports.mirrormax.net
 500 [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/universe Packages
     origin ubuntu-backports.mirrormax.net
 500 [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/main Packages
     origin ubuntu-backports.mirrormax.net
 500 [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/multiverse Packages
     release v=5.04,o=Ubuntu,a=hoary,l=Ubuntu,c=multiverse
     origin archive.ubuntu.com
 500 [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/universe Packages
     release v=5.04,o=Ubuntu,a=hoary-security,l=Ubuntu,c=universe
     origin security.ubuntu.com
 500 [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/restricted Packages
     release v=5.04,o=Ubuntu,a=hoary-security,l=Ubuntu,c=restricted
     origin security.ubuntu.com
 500 [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/main Packages
     release v=5.04,o=Ubuntu,a=hoary-security,l=Ubuntu,c=main
     origin security.ubuntu.com
 500 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/universe Packages
     release v=5.04,o=Ubuntu,a=hoary,l=Ubuntu,c=universe
     origin us.archive.ubuntu.com
 500 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/restricted Packages
     release v=5.04,o=Ubuntu,a=hoary,l=Ubuntu,c=restricted
     origin us.archive.ubuntu.com
 500 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main Packages
     release v=5.04,o=Ubuntu,a=hoary,l=Ubuntu,c=main
     origin us.archive.ubuntu.com
 991 [http://kubuntu.org](http://kubuntu.org) hoary-updates/main Packages
     origin kubuntu.org
 500 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates/restricted Packages
     release v=5.04,o=Ubuntu,a=hoary-updates,l=Ubuntu,c=restricted
     origin us.archive.ubuntu.com
 500 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates/main Packages
     release v=5.04,o=Ubuntu,a=hoary-updates,l=Ubuntu,c=main
     origin us.archive.ubuntu.com
 500 [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) hoary/restricted Packages
     release v=5.04,o=Ubuntu,a=hoary,l=Ubuntu,c=restricted
     origin br.archive.ubuntu.com
 500 [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) hoary/main Packages
     release v=5.04,o=Ubuntu,a=hoary,l=Ubuntu,c=main
     origin br.archive.ubuntu.com
 500 cdrom://Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407) hoary/restricted Packages
     release v=5.04,o=Ubuntu,a=hoary,l=Ubuntu,c=restricted
     origin Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)
 500 cdrom://Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407) hoary/main Packages
     release v=5.04,o=Ubuntu,a=hoary,l=Ubuntu,c=main
     origin Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)
Pacotes Pinados:

:)

---

### Post by raven on 2005-08-19
oi kheno did you try from synaptic/kynaptic
edit/fix broken packages 
it might help (sorry I did not read all the threads)

---

