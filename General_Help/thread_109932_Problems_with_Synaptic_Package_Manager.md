---
title: "Problems with Synaptic Package Manager"
date: 2005-12-29
forum: General Help
---

### Post by SuperDweeb on 2005-12-29
Hello,
I had several programs (Muine and F-Spot) recommended to me and they are both found in the Synaptic Package manager and the Add Applications utiltity.  But whenever I try to install these particular programs it gives me errors in both utilities.  I'll tell you what it says.
In Synaptic:
[I]**Could not Mark all packages for installation or upgrade**
The following packages have unresolvable dependencies.  Make sure that all required depositories are added and enabled in the preferences.

muine:
 Depends: libid3tag0 (>=0.15.1b) but it is not installable
 Depends: mono-jit (>=1.0) but it is not installable
 Depends: libdbus-1-cil (>=0.36.2) but it is not installable
 Depends: libgconf2.0-cil but it is not going to be installed
 Depends: libgconf2.0-cil but it is not going to be installed
 Depends: libglade2.0-cil but it is not going to be installed
 Depends: libglib2.0-cil but it is not going to be installed
 Depends: libgnome2.0-cil but it is not going to be installed
 Depends: libgtk2.0-cil but it is not going to be installed
 Depends: mono-classlib-1.0 (>=1.0) but it is not installable[/I]

And in the Add Applications:
[I]Cannot install 'muine'
Installing this application would mean that something else needs to be removed. Please use the "Advanced" mode to install 'muine'.[/I]

The same things happen when I try to install F-spot and quite a few other programs I've realized.  I have checked my repositories in Synaptic and they seem to be fine.  Any help you could give me would be appreciated.  Thanks!

---

### Post by Odinist on 2005-12-29
Sounds like you don't have all the proper repositories enabled...

Can you post what's in your sources.list? (/etc/apt/sources.list)

---

### Post by SuperDweeb on 2005-12-29
Okay, here is everything in the sources.list file:

[I]deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted


## Uncomment the following two lines to fetch updated software from the network
# deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
# deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted
# deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe


deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy multiverse universe
[/I]


Hope you see something here.

---

### Post by Odinist on 2005-12-29
Change it to this:

#deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted


## Uncomment the following two lines to fetch updated software from the network
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe


deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy multiverse universe

---

### Post by ykpaiha on 2005-12-29
U may uncheck all repositories + universe +multiverse + update
with : sudo gedit
(u better as well check (#) the cd line)
then apt-get update or in synaptic
....
all this if you have a good intenet connection of course

Sorry "druid" I didn't know you was here...

it seems that our newby "superdwzzb" forgot apt-get update?

---

### Post by SuperDweeb on 2005-12-29
Sorry, didn't work.  Now in Synaptic it gives me the message:

[I]Warning: The following problems were found on your system

W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-updates_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/restricted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-updates_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/restricted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/universe Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/multiverse Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_universe_binary-i386_Packages) - stat (2 No such file or directory)
[/I]

---

### Post by akiro.yamamoto on 2005-12-29
Try to Re-Load package information.
This should get the lists from the repositories.
I've encountered this problem once before, performing a re-load cleared it up... Go Figure
:smile:

---

### Post by SuperDweeb on 2005-12-29
Sorry guys, it didn't work.  It got rid of the warning message when I start up synaptic but now it is back to square one with the same message I originally got (check original post).  The refresh pulled up 51 new updates in my toolbar though if that has anything to do with it.

---

### Post by ykpaiha on 2005-12-29
close synaptic
open a console
inside type
1) sudo gedit /etc/apt/sources.list
2) change it like it has been said
3)close and save
4) in the console type again
sudo apt-get update
you will see a lot of lines going....
verify the errors message if any let us know
5) type again
sudo apt-get dist-upgrade -s
the "-s" will check the possibility to update everything without installing it
check errors message if any
retype apt-get dist-upgrade without the -s if it's ok for you
.....
welcome in a dirty world

---

### Post by SuperDweeb on 2005-12-29
Hmm... No go.  I didn't get any error messages.  When I completed the last step you gave me it said there was 61 MB of updates to my system it needed to download and since I'm on dial-up I don't really have the time to get all of it right now.  Do I need to?  Will that fix it? (Sorry, I'm very new to linux)

---

### Post by ykpaiha on 2005-12-29
unless your system is up to date you will get some problem with new installs

so better you update it belive me (or us ) it is is usualy without any trouble

sudo apt-get update
sudo apt-get dist-upgrade

go go go go!!!

---

### Post by Odinist on 2005-12-30
[QUOTE=ykpaiha]
sudo apt-get update
sudo apt-get dist-upgrade

go go go go!!![/QUOTE]

Amen brother! =D> [-o<

---

