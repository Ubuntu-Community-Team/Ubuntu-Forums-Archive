---
title: "E: Broken packages and unmet dependencies errors recently"
date: 2009-04-07
forum: General Help
---

### Post by anjames on 2009-04-07
Earlier today Adept popped up a notification in the tray saying that there were a number of updates. As I usually do, I brought the updater up and clicked 'apply' to install the updates and dismissed my concerns about packages marked for removal (MANY from kde, amarok2, konqueror, konsole, etc) assuming they would be replaced with some new version. They weren't replaced and in trying to reinstall them brings the following errors:

[INDENT]
root@amaterasu:/etc# apt-get install kubuntu-desktop
Reading package lists... Done
Building dependency tree
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  kubuntu-desktop: Depends: kde-window-manager but it is not going to be installed
                   Depends: kdebase-workspace-bin but it is not going to be installed
                   Depends: ksysguard but it is not going to be installed
                   Recommends: kate but it is not going to be installed
                   Recommends: kdebase-plasma but it is not going to be installed
                   Recommends: kdebluetooth but it is not going to be installed
                   Recommends: kdeplasma-addons but it is not going to be installed
                   Recommends: openoffice.org-kde but it is not going to be installed
                   Recommends: plasmoid-quickaccess but it is not going to be installed
E: Broken packages
[/INDENT]
I could swear that those 'dependencies' are supposed to be provided by kubuntu-desktop.


Searching the forums for "E: Broken packages" and "unmet dependencies" reveals a number of other users with similar problems and a couple of possibly related bug reports:

[http://ubuntuforums.org/showthread.php?t=1114928&highlight=E%3A+Broken+packages](http://ubuntuforums.org/showthread.php?t=1114928&highlight=E%3A+Broken+packages)
[http://ubuntuforums.org/showthread.php?t=1116991&highlight=E%3A+Broken+packages](http://ubuntuforums.org/showthread.php?t=1116991&highlight=E%3A+Broken+packages)
[http://ubuntuforums.org/showthread.php?t=1111860&highlight=E%3A+Broken+packages](http://ubuntuforums.org/showthread.php?t=1111860&highlight=E%3A+Broken+packages)
[http://ubuntuforums.org/showthread.php?t=1116466&highlight=E%3A+Broken+packages](http://ubuntuforums.org/showthread.php?t=1116466&highlight=E%3A+Broken+packages)
[http://ubuntuforums.org/showthread.php?t=1116132&highlight=E%3A+Broken+packages](http://ubuntuforums.org/showthread.php?t=1116132&highlight=E%3A+Broken+packages)
[http://ubuntuforums.org/showthread.php?t=1115813&highlight=E%3A+Broken+packages](http://ubuntuforums.org/showthread.php?t=1115813&highlight=E%3A+Broken+packages)
[http://ubuntuforums.org/showthread.php?t=1115828&highlight=E%3A+Broken+packages](http://ubuntuforums.org/showthread.php?t=1115828&highlight=E%3A+Broken+packages)

[https://bugs.launchpad.net/ubuntu/+source/kde4libs/+bug/354927?comments=all](https://bugs.launchpad.net/ubuntu/+source/kde4libs/+bug/354927?comments=all)

They all have appeared in the forums in the past week, but otherwise I'm not sure about the connection. Usually I'm pretty good at getting to the bottom of these things, but I'm drawing a blank. Did something go into the apt servers which shouldn't have?

In case it helps, here's my sources.list:
[INDENT]root@amaterasu:/etc/apt# cat sources.list                                                                                                                                                         
# Latest wine                                                                                                                                                                                     
#deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) intrepid main universe multiverse                                                                                                                        
#deb-src [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) intrepid main universe multiverse                                                                                                                    

# OpenOffice 3 repository
#deb [http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu) intrepid main universe multiverse

# Amarok 2 (amarok-kde4) repository
#deb [http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu](http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu) intrepid main universe multiverse

# Google repository
deb [http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/) stable non-free
deb [http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/) testing non-free


# deb cdrom:[Kubuntu-KDE4 8.04 _Hardy Heron_ - Release i386 (20080423)]/ hardy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to                     
# newer versions of the distribution.

deb [http://mirrors.us.kernel.org/ubuntu/](http://mirrors.us.kernel.org/ubuntu/) intrepid main restricted
deb-src [http://mirrors.us.kernel.org/ubuntu/](http://mirrors.us.kernel.org/ubuntu/) intrepid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://mirrors.us.kernel.org/ubuntu/](http://mirrors.us.kernel.org/ubuntu/) intrepid-updates main restricted
deb-src [http://mirrors.us.kernel.org/ubuntu/](http://mirrors.us.kernel.org/ubuntu/) intrepid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://mirrors.us.kernel.org/ubuntu/](http://mirrors.us.kernel.org/ubuntu/) intrepid universe
deb-src [http://mirrors.us.kernel.org/ubuntu/](http://mirrors.us.kernel.org/ubuntu/) intrepid universe
deb [http://mirrors.us.kernel.org/ubuntu/](http://mirrors.us.kernel.org/ubuntu/) intrepid-updates universe
deb-src [http://mirrors.us.kernel.org/ubuntu/](http://mirrors.us.kernel.org/ubuntu/) intrepid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://mirrors.us.kernel.org/ubuntu/](http://mirrors.us.kernel.org/ubuntu/) intrepid multiverse
deb-src [http://mirrors.us.kernel.org/ubuntu/](http://mirrors.us.kernel.org/ubuntu/) intrepid multiverse
deb [http://mirrors.us.kernel.org/ubuntu/](http://mirrors.us.kernel.org/ubuntu/) intrepid-updates multiverse
deb-src [http://mirrors.us.kernel.org/ubuntu/](http://mirrors.us.kernel.org/ubuntu/) intrepid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://mirrors.us.kernel.org/ubuntu/](http://mirrors.us.kernel.org/ubuntu/) intrepid-security main restricted
deb-src [http://mirrors.us.kernel.org/ubuntu/](http://mirrors.us.kernel.org/ubuntu/) intrepid-security main restricted
deb [http://mirrors.us.kernel.org/ubuntu/](http://mirrors.us.kernel.org/ubuntu/) intrepid-security universe
deb-src [http://mirrors.us.kernel.org/ubuntu/](http://mirrors.us.kernel.org/ubuntu/) intrepid-security universe
deb [http://mirrors.us.kernel.org/ubuntu/](http://mirrors.us.kernel.org/ubuntu/) intrepid-security multiverse
deb-src [http://mirrors.us.kernel.org/ubuntu/](http://mirrors.us.kernel.org/ubuntu/) intrepid-security multiverse
[/INDENT]

---

### Post by hyper_ch on 2009-04-07
Your sources list is quite mixed and hard to read. My I suggest you generate a new one using my generator in my sig?

---

### Post by anjames on 2009-04-07
Your repository generator isn't working for me at the moment

It looks like somehow kubuntu-desktop got marked for removal even!


root@amaterasu:/etc/apt# apt-cache policy kubuntu-desktop
kubuntu-desktop:
  Installed: (none)
  Candidate: 1.101
  Version table:
     1.101 0
        500 [http://mirrors.us.kernel.org](http://mirrors.us.kernel.org) intrepid/main Packages


So how would I reinstall it then? Why does it say kubuntu-desktop depends on those three packages but they aren't going to be installed? I thought apt was supposed to resolve dependencies and install whatever you need?

Argh.

---

### Post by hyper_ch on 2009-04-07
my generator is working for me.

---

### Post by anjames on 2009-04-07
Most likely it's a problem on my side. Most of kubuntu was uninstalled by Adept I've been having some problems. For clarity, here is a revised (hopefully equivalent) sources.list:

[INDENT][FONT="Courier New"]
root@amaterasu:/etc/apt# cat sources.list
deb     [http://mirrors.us.kernel.org/ubuntu/](http://mirrors.us.kernel.org/ubuntu/) intrepid          main restricted universe multiverse
deb-src [http://mirrors.us.kernel.org/ubuntu/](http://mirrors.us.kernel.org/ubuntu/) intrepid          main restricted universe multiverse
deb     [http://mirrors.us.kernel.org/ubuntu/](http://mirrors.us.kernel.org/ubuntu/) intrepid-updates  main restricted universe multiverse
deb-src [http://mirrors.us.kernel.org/ubuntu/](http://mirrors.us.kernel.org/ubuntu/) intrepid-updates  main restricted universe multiverse
deb     [http://mirrors.us.kernel.org/ubuntu/](http://mirrors.us.kernel.org/ubuntu/) intrepid-security main restricted universe multiverse
deb-src [http://mirrors.us.kernel.org/ubuntu/](http://mirrors.us.kernel.org/ubuntu/) intrepid-security main restricted universe multiverse

# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse

# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner

# Latest wine
#deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt)     intrepid main universe multiverse
#deb-src [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) intrepid main universe multiverse

# OpenOffice 3
#deb [http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu) intrepid main universe multiverse

# Amarok 2 (amarok-kde4)
#deb [http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu](http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu) intrepid main universe multiverse

# Google repository (picasa, etc)
#deb [http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/) stable  non-free
#deb [http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/) testing non-free

[/FONT]
[/INDENT]

---

### Post by anjames on 2009-04-08
Fixed. Comment excerpt from this bug report:
[https://bugs.launchpad.net/ubuntu/+source/kde4libs/+bug/354927?comments=all](https://bugs.launchpad.net/ubuntu/+source/kde4libs/+bug/354927?comments=all)

...


It apparently depends on a version of kdelibs5-data which isn't available via even with the backports repository enabled (do you have to specify the backport version?). Manual installation via

root@amaterasu:/etc/apt# dpkg -i /home/user/Desktop/kdelibs5-data_4.2.0-0ubuntu2~intrepid2_all.deb

fixed many of the 'Depends' errors. Now I have only:

root@amaterasu:/etc/apt# apt-get install kubuntu-desktop
Reading package lists... Done
Building dependency tree
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  kubuntu-desktop: Depends: kdebase-workspace-bin but it is not going to be installed
                   Recommends: openoffice.org-kde but it is not going to be installed
E: Broken packages

OK, I think I've got it fixed. apt-get is at least downloading and apparently reinstalling kubuntu-desktop anyway! In summary the two packages I needed from backports to fix this were:

kdebase-workspace-data_4.2.0-0ubuntu7~intrepid1_all.deb
kdelibs5-data_4.2.0-0ubuntu2~intrepid2_all.deb

I manually installed them via dpkg -i, as apt-get didn't seem to want to despite my uncommenting the backports repository in my sources.list.

The bottom line seems to be that kubuntu-desktop packages in the main repository should depend only on packages in the main repository so users don't have to use packages from the backports repo.

---

