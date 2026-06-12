---
title: "Add/Remove Applications is empty"
date: 2008-12-24
forum: General Help
---

### Post by spinstartshere on 2008-12-24
I cannot use the Add/Remove app because there are no programs in it.  Synaptic works fine as far as I can tell.  Help, please!

---

### Post by northern lights on 2008-12-24
Have you tried adjusting the "Show:" drop down menu? Say to "All available applications", for instance?

---

### Post by spinstartshere on 2008-12-24
There would be items in the list, regardless of which option is selected.  It just says in the lower box that there are no matching applications available.

---

### Post by northern lights on 2008-12-24
The Add/Remove applications dialog is called *gnome-app-install*. I'd recommend purging it and giving a reinstall a try, but unfortunately it's part of the meta-package *ubuntu-desktop* and will uthus cause a whole lot more to be removed if you're trying to purge it.

However, it uses apt-get as a backend also, as does Synaptic.

Have you tried simply running```
sudo apt-get update
```and checking again?

Are you certain Synaptic's working?

Can you post the output of ```
cat /etc/apt/sources.list
```Thank you.

---

### Post by spinstartshere on 2008-12-24
I know Synaptic works because I've had no choice but to use it to install and uninstall applications.

/etc/apt/sources.list:
```

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.

deb http://archive.canonical.com/ubuntu intrepid partner
deb http://archive.ubuntu.com/ubuntu/ intrepid main universe restricted multiverse
deb-src http://archive.ubuntu.com/ubuntu/ intrepid universe main multiverse restricted #Added by software-properties
deb http://security.ubuntu.com/ubuntu/ intrepid-security universe main multiverse restricted
deb-src http://archive.ubuntu.com/ubuntu/ intrepid-security universe main multiverse restricted
deb http://archive.ubuntu.com/ubuntu/ intrepid-updates universe main multiverse restricted
deb-src http://archive.ubuntu.com/ubuntu/ intrepid-updates universe main multiverse restricted
deb http://archive.ubuntu.com/ubuntu/ intrepid-backports universe main multiverse restricted
deb-src http://archive.ubuntu.com/ubuntu/ intrepid-backports universe main multiverse restricted

# deb http://people.ubuntu.com/~pitti/ddebs hardy main universe

deb-src http://us.archive.ubuntu.com/ubuntu hardy-updates multiverse

deb-src http://us.archive.ubuntu.com/ubuntu intrepid-updates multiverse

deb http://us.archive.ubuntu.com/ubuntu intrepid-updates multiverse

deb-src http://us.archive.ubuntu.com/ubuntu intrepid multiverse

deb http://us.archive.ubuntu.com/ubuntu intrepid multiverse

deb-src http://security.ubuntu.com/ubuntu intrepid-security multiverse

deb-src http://security.ubuntu.com/ubuntu intrepid-security universe

deb-src http://security.ubuntu.com/ubuntu intrepid-security main restricted

deb-src http://archive.canonical.com/ubuntu intrepid partner

deb http://dl.google.com/linux/deb/ stable non-free
deb http://dl.google.com/linux/deb/ testing non-free
deb http://ppa.launchpad.net/openoffice-pkgs/ubuntu intrepid main
deb http://deb.opera.com/opera/ lenny non-free #Opera
deb http://download.skype.com/linux/repos/debian stable non-free #Skype
deb http://ppa.launchpad.net/rvm/ubuntu intrepid main
deb http://ppa.launchpad.net/transmissionbt/ubuntu intrepid main
deb http://ppa.launchpad.net/banshee-team/ubuntu intrepid main
deb http://ppa.launchpad.net/tualatrix/ubuntu intrepid main
deb http://ppa.launchpad.net/teknoraver/ubuntu hardy main
deb-src http://ppa.launchpad.net/teknoraver/ubuntu hardy main
deb http://ppa.launchpad.net/medigeek/ubuntu intrepid main
deb http://ppa.launchpad.net/transmissionbt-beta/ubuntu intrepid main
deb http://wine.budgetdedicated.com/apt intrepid main #WineHQ - Ubuntu 8.10 "Intrepid Ibex"
```

---

### Post by northern lights on 2008-12-24
I was hoping it'd be empty at best or missing some repositories. That is unfortunately not the case.

I'd remove both the commented and uncommented hardy entries and clean it up a bit, but neither it's messy character or the hardy entries should effect gnome-app-install and gnome-app-install only.

If Synaptic's working fine, so should gnome-app-install.

I wonder how to diagnose this, I'm a bit stumped.

---

### Post by northern lights on 2008-12-24
Due to a lack of ideas and for shits & giggles, I've cleaned it up, removed duplicate and hardy entries and commented all the personal launchpad repositories as well as the backports. I'd suggest making a backup of yours and replacing it with this:```
deb http://archive.ubuntu.com/ubuntu/ intrepid main universe restricted multiverse
deb-src http://archive.ubuntu.com/ubuntu/ intrepid universe main multiverse restricted

deb http://security.ubuntu.com/ubuntu/ intrepid-security universe main multiverse restricted
deb-src http://security.ubuntu.com/ubuntu/ intrepid-security universe main multiverse restricted

deb http://archive.ubuntu.com/ubuntu/ intrepid-updates universe main multiverse restricted
deb-src http://archive.ubuntu.com/ubuntu/ intrepid-updates universe main multiverse restricted

deb http://archive.canonical.com/ubuntu intrepid partner

# deb http://archive.ubuntu.com/ubuntu/ intrepid-backports universe main multiverse restricted
# deb-src http://archive.ubuntu.com/ubuntu/ intrepid-backports universe main multiverse restricted

# deb http://dl.google.com/linux/deb/ stable non-free
# deb http://dl.google.com/linux/deb/ testing non-free
# deb http://ppa.launchpad.net/openoffice-pkgs/ubuntu intrepid main
# deb http://deb.opera.com/opera/ lenny non-free #Opera
# deb http://download.skype.com/linux/repos/debian stable non-free #Skype
# deb http://ppa.launchpad.net/rvm/ubuntu intrepid main
# deb http://ppa.launchpad.net/transmissionbt/ubuntu intrepid main
# deb http://ppa.launchpad.net/banshee-team/ubuntu intrepid main
# deb http://ppa.launchpad.net/tualatrix/ubuntu intrepid main
# deb http://ppa.launchpad.net/teknoraver/ubuntu hardy main
# deb-src http://ppa.launchpad.net/teknoraver/ubuntu hardy main
# deb http://ppa.launchpad.net/medigeek/ubuntu intrepid main
# deb http://ppa.launchpad.net/transmissionbt-beta/ubuntu intrepid main
# deb http://wine.budgetdedicated.com/apt intrepid main

```

I doubt it's going to fix your *gnome-app-install*, but I wouldn't leave it untried.

---

### Post by spinstartshere on 2008-12-24
It had the effect I expected, which was none.  I cannot understand how the repositories list file would cause the Add/Remove app to show no entries.  I am wondering whether installing KDE4 may have had an effect on it.

---

### Post by northern lights on 2008-12-24
Are you currently running a gnome or a KDE desktop???

I'm telling you, I'm stumped as to what might have caused it.

For temporary ease, if you dislike searching Synaptic, check [http://packages.ubuntu.com/]("http://packages.ubuntu.com/") for an overview over the repositories and install directly via *aptitude* or *apt-get*. Sorry man, I'm clueless.

---

### Post by spinstartshere on 2008-12-24
I'm using GNOME.  I did not like KDE4 because of how out of place GNOME applications look in it.  I do not have a problem with using Synaptic, but the Add/Remove app is easier to use for some things.

---

### Post by plucky on 2008-12-24
Have you tried re-installing the application? 


Seems to have fixed the problem in this [thread](http://ubuntuforums.org/showthread.php?t=1016743&highlight=add%2Fremove+empty)


Good Luck

---

### Post by spinstartshere on 2008-12-24
Doing that fixed my problem, thank you.  I believe the cause of the problem was the same as well.

---

### Post by Coder543 on 2008-12-24
I have a suggestion, two in fact.

First, go to gnome-app-install in synaptic.
click the box to the left of it and tell it to reinstall it.
click apply.
after it finished go to the top of synaptic and click reload.
now go to add/remove.

Does it work?

If not, press Ctrl + Alt + F1
type your user name
press enter
type your password (it will not appear)
press enter

(Obligatory Warning: Make sure your data is backed up, this coming part might get... hairy)

type sudo apt-get remove ubuntu-desktop gnome-app-install
press enter
type your password (it will not appear)
press enter
let it finish
type sudo apt-get install ubuntu-desktop gnome-app-install
press enter
you may (or may not) have to type your password
let it finish
type sudo gdm
you may (or may not) have to type your password
login to the gui
try it out.





edit:  nvm, only saw first page.

---

