---
title: "Repository Trouble"
date: 2009-02-05
forum: General Help
---

### Post by a_toff on 2009-02-05
Hi there,

I'm having trouble updating my package lists from the repositories I have enabled.

I have tried updating from a number of different servers, including servers suggested by the "Select Best Server" function. I get good speeds on some of the packages, but I always end up with error messages.

```
W: Failed to fetch http://packages.freecontrib.org/plf/dists/intrepid/Release.gpg  Could not connect to packages.freecontrib.org:80 (34.52.53.34), connection timed out

W: Failed to fetch http://packages.freecontrib.org/plf/dists/intrepid/free/i18n/Translation-en_CA.bz2  Unable to connect to packages.freecontrib.org http:

W: Failed to fetch http://packages.freecontrib.org/plf/dists/intrepid/non-free/i18n/Translation-en_CA.bz2  Unable to connect to packages.freecontrib.org http:

W: Failed to fetch http://archive.canonical.com/ubuntu/dists/intrepid-commercial/main/binary-amd64/Packages.gz  404 Not Found

W: Some index files failed to download, they have been ignored, or old ones used instead.

```


This is my sources.list file:

```
# deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release amd64 (20081029.2)]/ intrepid main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://archive.ubuntu.com/ubuntu/ intrepid restricted main
deb-src http://archive.ubuntu.com/ubuntu/ intrepid restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu/ intrepid-updates restricted main
deb-src http://archive.ubuntu.com/ubuntu/ intrepid-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu/ intrepid universe
deb http://archive.ubuntu.com/ubuntu/ intrepid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu.com/ubuntu/ intrepid multiverse
deb http://archive.ubuntu.com/ubuntu/ intrepid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://ca.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse
# deb-src http://ca.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu intrepid partner
deb-src http://archive.canonical.com/ubuntu intrepid partner

deb http://archive.ubuntu.com/ubuntu/ intrepid-security restricted main
deb-src http://archive.ubuntu.com/ubuntu/ intrepid-security restricted main multiverse universe #Added by software-properties
deb http://archive.ubuntu.com/ubuntu/ intrepid-security universe
deb http://archive.ubuntu.com/ubuntu/ intrepid-security multiverse
deb http://ppa.launchpad.net/openoffice-pkgs/ubuntu intrepid main
deb http://archive.canonical.com/ubuntu intrepid-commercial main
deb http://packages.freecontrib.org/plf intrepid free non-free
deb-src http://packages.freecontrib.org/plf intrepid free non-free
deb http://archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse #Added by software-properties
```

Is there something that I'm missing? Maybe the repos above aren't the problem, but I'm currently in the middle of a re-installation of my system... I'm trying to get wacom support back for my tablet and need to download some packages which are not seen when doing the "apt-get install" command, as well as trying to get the celestia-common-nonfree package, which doesn't show-up in my search results in Synaptic.

help!

---

### Post by drs305 on 2009-02-05
Having the error messages would be helpful, but I used your sources.list and had problems with the *freecontrib* and canonical's *intrepid-commerical* repositories. You might be getting errors on the *launchpad* because they recently have started signing their packages. You might need to import the keys to get that to work. If this is the case you would get an error message with the key code.

If you don't need files from those repositories, the short-term fix would be to place a comment symbol in front of the *"freecontrib" and canonical's "intrepid-commercial"* repositories and import the key for the ppa one. 
```

sudo cp /etc/apt/sources.list /etc/apt/sources.list.bak
gksudo gedit /etc/apt/sources.list

```

If you provide the specific error messages we can probably provide better solutions.

---

### Post by a_toff on 2009-02-05
> **drs305 said:**
> Having the error messages would be helpful, but I used your sources...

thanks... I've edited my post above to include the error messages.

I've made some progress... not sure what did but I was able to download the wacom files I needed.But Synaptic is still not seeing the Celestia packages. Might I be missing the appropriate repo? How does one find out which repos are associated with which software?

---

### Post by drs305 on 2009-02-05
> **a_toff said:**
> But Synaptic is still not seeing the Celestia packages. Might I be missing the appropriate repo? How does one find out which repos are associated with which software?

Visit this site if it's in the ubuntu repositories:
[http://packages.ubuntu.com/]("http://packages.ubuntu.com/")

There is a search link about 1/5 of the way down the page. Choose the version you have and the package your are interested in. It says 'celestia' is in the intrepid "universe" repository. Make sure "universe" is enabled: synaptic or 'software sources' > Settings > Repositories > Ubuntu Software > check "universe".

---

### Post by a_toff on 2009-02-05
> **drs305 said:**
> Visit this site if it's in the ubuntu repositories:
[http://packages.ubuntu.com/]("http://packages.ubuntu.com/")

There is a search link about 1/5 of the way down the page. Choose the version you have and the package your are interested in. It says 'celestia' is in the intrepid "universe" repository. Make sure "universe" is enabled: synaptic or 'software sources' > Settings > Repositories > Ubuntu Software > check "universe".

In 'Software Sources' > Ubuntu Software I have five options available, all of which are "checked":

- Canonical-supported Open Source software (main)
- Community-maintained Open Source software (universe)
- Proprietary drivers for devices (restricted)
- Software restricted by copyright or legal issues (multiverse)
- Source Code

Download from: Main Server


And still, when I enter "celestia" in the quick-search in Synaptic, I return no results.

---

### Post by Partyboi2 on 2009-02-05
Make sure that in the left pane window of Synaptic that you have selected "All" when doing a search for celestia. If it is highlighting one of the other ones like "Installed" you will not see anything when searching for celestia.

---

### Post by forger on 2009-02-07
The freecontrib doesn't work at all:
[http://packages.freecontrib.org/plf/dists/intrepid/Release.gpg](http://packages.freecontrib.org/plf/dists/intrepid/Release.gpg)
> Failed to Connect
The connection was refused when attempting to contact packages.freecontrib.org.

You should contact them about this, maybe they've shut it down.

Also, "intrepid-commercial" doesn't exist.


For PPA links and their GPG keys, read: [http://ubuntuforums.org/showthread.php?t=1056099](http://ubuntuforums.org/showthread.php?t=1056099)

---

### Post by rasmus91 on 2009-02-24
> I have tried updating from a number of different servers, including servers suggested by the "Select Best Server" function. I get good speeds on some of the packages, but I always end up with error messages.

Its not always the servers thats the problem, make sure you're connected to a network which allows you to use these ports

---

