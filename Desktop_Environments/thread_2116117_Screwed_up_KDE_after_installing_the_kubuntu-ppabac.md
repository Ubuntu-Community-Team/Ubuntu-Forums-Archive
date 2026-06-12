---
title: "Screwed up KDE after installing the kubuntu-ppa/backports PPA"
date: 2013-02-14
forum: Desktop Environments
---

### Post by Stonecold1995 on 2013-02-14
I added the kubuntu-ppa/backports PPA so I could get the newest versions of KDE packages, however, after upgrading, plasma-desktop seems to have been removed, but not re-installed (upgraded) like all the other packages.  I tried running this:
```
alex@kubuntu:~$ sudo apt-get install plasma-desktop
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 plasma-desktop : Depends: plasma-widgets-workspace (= 4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
```So then I tried
```
alex@kubuntu:~$ sudo apt-get install plasma-widgets-workspace
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 plasma-widgets-workspace : Depends: akonadi-server but it is not going to be installed
                            Depends: kdepim-runtime but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
```kdepim-runtime only requires akonadi-server, so I tried installing that:
```
alex@kubuntu:~$ sudo apt-get install akonadi-server
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 akonadi-server : Depends: libboost-program-options1.48.0 (>= 1.48.0-1) but it is not installable
E: Unable to correct problems, you have held broken packages.
```However, no matter what version of libboost-programs-options I have installed, I still get the above problem when trying to install akonadi-server!  Currently I have libboost-program-options1.49.0 and libboost-program-options1.49.0-dev.

**How can I get akonadi-server installed so I can have plasma-desktop back!?**


Also, System Settings seems to have lost a few entries...  For me, it now looks like this:
[[IMG]http://www.pictureshack.us/thumbs/14442_systemsettings.png[/IMG]]("http://www.pictureshack.us/images/14442_systemsettings.png")
When I get plasma-desktop installed, the old entries (I think they are related to plasma-desktop) will come back, right?

It's so annoying that the only package for updating KDE breaks plasma-desktop itself, and even "sudo apt-get -f install" won't fix it...






**EDIT:** I managed to install plasma-desktop (and all its dependencies), so now plasma-desktop seems like it's working, but I still have the problem that all the plasma-desktop utilities (or whatever they're called) aren't here.  Like, I don't have the KickOff menu (or the WHOLE bottom menu), I can't right click on my wallpaper to bring up options, etc.  How do I get those back???

---

### Post by Stonecold1995 on 2013-02-14
Well, disregard mostly what I said, it's "sort of" working now, but EVERY widget is gone!  This is what the bottom menu bar looks like:

[[IMG]http://www.pictureshack.us/thumbs/90752_no_widgets_1.png[/IMG]]("http://www.pictureshack.us/images/90752_no_widgets_1.png")

When I select "Add Widgets", the bar changes to this (usually it has a list of widgets):

[[IMG]http://www.pictureshack.us/thumbs/73972_no_widgets_2.png[/IMG]]("http://www.pictureshack.us/images/73972_no_widgets_2.png")

When I hover over the red [X], this pops up:

[IMG]http://www.pictureshack.us/images/80061_no_widgets_3.png[/IMG]

I assume this is what's preventing all the try icons from appearing?  How do I fix this?

I just want to be able to have my icons back now, klipper, Network manager, etc...

**Another edit:** A difference between my computer and my brother's (which has not been updated with this PPA) is that my computer now lacks plasma-widgets-addons.  I tried installing it and got this:
```
alex@kubuntu:/tmp$ sudo apt-get install plasma-widgets-addons
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:

 plasma-widgets-addons : Depends: libkexiv2-11 but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
```libkexiv2-11 depends on libexiv2-11, however, I've already installed libexiv2-11 from a downloaded .deb file (apt-get couldn't find it), so I get this:

```
alex@kubuntu:/tmp$ sudo apt-get install libexiv2-11
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libexiv2-11:i386 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 7 not upgraded.
```Why in the world is libkexiv2-11 not being installed, even though its dependency seems to be installed?  Without libkexiv2-11, I can't install plasma-widgets-addons so I can't even TELL if that's what's causing the problem!  This is frustrating me so much! :mad:

---

### Post by carl4926 on 2013-02-14
Did you try deleting the panel and then add one back?

Widgets must be unlocked
Delete panel
Then right click Add > Panel > Default Panel

---

### Post by Stonecold1995 on 2013-02-14
> **carl4926 said:**
> Did you try deleting the panel and then add one back?

Widgets must be unlocked
Delete panel
Then right click Add > Panel > Default Panel
Yes, I tried deleting it and adding it again, the red [X] is still there in place of all my tray icons.


Here's more info.  When I upgraded, a few packages were being held back, when I tried to upgrade them individually, this happened:
```
alex@kubuntu:/var/lib/apt/lists$ sudo apt-get install gwenview kde-runtime kde-runtime-dbg ksnapshot nepomuk-core okular plasma-scriptengine-javascript
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:

 gwenview : Depends: libexiv2-11 but it is not installable
 kde-runtime : Depends: libexiv2-11 but it is not installable
 ksnapshot : Depends: libkipi8 (>= 4:4.7.90) but it is not installable
 nepomuk-core : Depends: libexiv2-11 but it is not installable
                Depends: libpoppler-qt4-3 (>= 0.18) but it is not installable
 okular : Depends: libpoppler-qt4-3 (>= 0.18) but it is not installable
E: Unable to correct problems, you have held broken packages.
```

And of course, with my bad luck they all have newer versions installed, so I have no idea how to get those packages to work. :mad:

---

### Post by carl4926 on 2013-02-14
Open up synaptic and check for broken packages
(You may need to install it)

---

### Post by Stonecold1995 on 2013-02-14
> **carl4926 said:**
> Open up synaptic and check for broken packages
(You may need to install it)
No broken packages.  This may already be obvious (or completely wrong), but I think the problem is that the packages that couldn't be upgraded (gwenview kde-runtime kde-runtime-dbg ksnapshot nepomuk-core okular plasma-scriptengine-javascript) require dependencies that are old, but all the other upgraded packages require the newest versions, and the dependencies can't co-oexist.

---

### Post by carl4926 on 2013-02-14
I suggest you also take your question to kubuntu forum.
I don't use the backports
And my KDE is openSUSE, which is running kde4.10 perfectly

For the upgrade, did you do

```
sudo apt-get update && dist-upgrade
```

---

### Post by Stonecold1995 on 2013-02-15
> **carl4926 said:**
> I suggest you also take your question to kubuntu forum.
I don't use the backports
And my KDE is openSUSE, which is running kde4.10 perfectly

For the upgrade, did you do

```
sudo apt-get update && dist-upgrade
```
Yes I did.  Maybe 4.10 is just too new and unstable for Kubuntu, should I just go with kubuntu-ppa/beta instead?

---

### Post by Stonecold1995 on 2013-02-15
Oh great...  I tried removing the PPA and adding the older beta one instead.  I updated, then tried dist-upgrade:
```
alex@kubuntu:~$ sudo apt-get install kubuntu-desktop
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 kubuntu-desktop : Depends: plasma-netbook but it is not going to be installed
                   Recommends: akregator but it is not going to be installed
                   Recommends: kaddressbook but it is not going to be installed
                   Recommends: kmail but it is not going to be installed
                   Recommends: kontact but it is not going to be installed
                   Recommends: korganizer but it is not going to be installed
                   Recommends: plasma-widgets-addons but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
```

So now I can't even go back, I'm stuck even though I tried changing the PPA?  How do revert changes?

---

### Post by carl4926 on 2013-02-15
Can you create and test a new user login

Also FYI: [http://www.kubuntu.org/news/kde-sc-4.10](http://www.kubuntu.org/news/kde-sc-4.10)

---

### Post by Stonecold1995 on 2013-02-15
> **carl4926 said:**
> Can you create and test a new user login

Also FYI: [http://www.kubuntu.org/news/kde-sc-4.10](http://www.kubuntu.org/news/kde-sc-4.10)

I can log in already.  Right now all I'm trying to do is revert the changes and go back to the old version of KDE, but it won't let me!  Now I tried this:
```
alex@kubuntu:~$ sudo apt-get install akonadi-server apport-kde apturl-kde jockey-kde kde-config-touchpad kde-workspace kde-workspace-bin kdepim-runtime kscreensaver kscreensaver-xsavers kubuntu-desktop kubuntu-notification-helper language-selector-kde libkgapi0 libkolab0 libmarblewidget14 libmuonprivate1 muon-installer muon-notifier muon-updater plasma-desktop plasma-netbook plasma-scriptengine-python plasma-scriptengines plasma-widget-facebook plasma-widgets-workspace printer-applet python-kde4 python3-pykde4 software-properties-kde system-config-printer-kde ubuntu-release-upgrader-qt update-manager-kde userconfig
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libkolab0 is already the newest version.
libkolab0 set to manually installed.
akonadi-server is already the newest version.
libkgapi0 is already the newest version.
libkgapi0 set to manually installed.
kde-workspace-bin is already the newest version.
kde-workspace-bin set to manually installed.
kde-workspace is already the newest version.
kde-workspace set to manually installed.
plasma-widgets-workspace is already the newest version.
plasma-widgets-workspace set to manually installed.
plasma-desktop is already the newest version.
kdepim-runtime is already the newest version.
kdepim-runtime set to manually installed.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 plasma-netbook : Depends: libkephal4abi1 (= 4:4.9.98a-0ubuntu1~ubuntu12.10~ppa1) but 4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1 is to be installed
                  Depends: libplasmagenericshell4 (= 4:4.9.98a-0ubuntu1~ubuntu12.10~ppa1) but 4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1 is to be installed
                  Depends: plasma-widgets-workspace (= 4:4.9.98a-0ubuntu1~ubuntu12.10~ppa1) but 4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1 is to be installed
E: Unable to correct problems, you have held broken packages.
```
How is it not downgrading them?  I tried reinstalling it instead:

```
alex@kubuntu:~$ sudo apt-get install --reinstall akonadi-server apport-kde apturl-kde jockey-kde kde-config-touchpad kde-workspace kde-workspace-bin kdepim-runtime kscreensaver kscreensaver-xsavers kubuntu-desktop kubuntu-notification-helper language-selector-kde libkgapi0 libkolab0 libmarblewidget14 libmuonprivate1 muon-installer muon-notifier muon-updater plasma-desktop plasma-netbook plasma-scriptengine-python plasma-scriptengines plasma-widget-facebook plasma-widgets-workspace printer-applet python-kde4 python3-pykde4 software-properties-kde system-config-printer-kde ubuntu-release-upgrader-qt update-manager-kde userconfig
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reinstallation of kde-workspace-bin is not possible, it cannot be downloaded.
Reinstallation of kde-workspace is not possible, it cannot be downloaded.
Reinstallation of plasma-widgets-workspace is not possible, it cannot be downloaded.
Reinstallation of plasma-desktop is not possible, it cannot be downloaded.
Reinstallation of kdepim-runtime is not possible, it cannot be downloaded.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 plasma-netbook : Depends: libkephal4abi1 (= 4:4.9.98a-0ubuntu1~ubuntu12.10~ppa1) but 4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1 is to be installed
                  Depends: libplasmagenericshell4 (= 4:4.9.98a-0ubuntu1~ubuntu12.10~ppa1) but 4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1 is to be installed
                  Depends: plasma-widgets-workspace (= 4:4.9.98a-0ubuntu1~ubuntu12.10~ppa1) but 4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1 is to be installed
E: Unable to correct problems, you have held broken packages.
```
What does it mean it mean they could not be downloaded?

So now I can't remove KDE, I can't downgrade it, nothing's working!

---

### Post by zombifier25 on 2013-02-15
If you just remove a PPA, then its packages are still in the system. Use ppa-purge to completely remove a PPA. It does not just remove the PPA, it also degrades all the packages form the PPA installed in your system to its repo version.
```
sudo apt-get install ppa-purge
```

To use it:
```
sudo ppa-purge ppa:kubuntu-ppa/beta
```
Or any PPA you want. I suggest you purge all KDE-related PPA and try again.

---

### Post by Stonecold1995 on 2013-02-15
> **zombifier25 said:**
> If you just remove a PPA, then its package are still in the system. Use ppa-purge to completely remove a PPA. It does not just remove the PPA, it also degrades all the packages form the PPA installed in your system to its repo version.
```
sudo apt-get install ppa-purge
```To use it:
```
sudo ppa-purge ppa:kubuntu-ppa/beta
```Or any PPA you want. I suggest you purge all KDE-related PPA and try again.

I tried ppa-purge with backports.  I just tried it now with beta as you suggested, and got this:
```
alex@kubuntu:~$ sudo ppa-purge ppa:kubuntu-ppa/beta
Updating packages lists
W: Failed to fetch http://ppa.launchpad.net/jonls/redshift-ppa/ubuntu/dists/quantal/main/source/Sources  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/jonls/redshift-ppa/ubuntu/dists/quantal/main/binary-amd64/Packages  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/jonls/redshift-ppa/ubuntu/dists/quantal/main/binary-i386/Packages  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/ubuntu-clamav/ppa/ubuntu/dists/quantal/main/source/Sources  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/ubuntu-clamav/ppa/ubuntu/dists/quantal/main/binary-amd64/Packages  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/ubuntu-clamav/ppa/ubuntu/dists/quantal/main/binary-i386/Packages  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.
Warning:  apt-get update failed for some reason
PPA to be removed: kubuntu-ppa beta
comm: file 2 is not in sorted order
Package revert list generated:
 kdevelop-l10n/quantal kdevelop-php-docs-l10n/quantal kdevelop-php-l10n/quantal 
libsyndication4/quantal libtaskmanager4abi3/quantal libthreadweaver4/quantal 
libweather-ion6/quantal marble-data/quantal marble-plugins/quantal 
nepomuk-core/quantal nepomuk-core-data/quantal nepomuk-core-dev/quantal 
okular/quantal okular-extra-backends/quantal oxygen-icon-theme/quantal 
plasma-containments-addons/quantal plasma-dataengines-addons/quantal 
plasma-dataengines-workspace/quantal plasma-desktop/quantal                                                                                                                                                 
plasma-desktopthemes-artwork/quantal plasma-runners-addons/quantal                                                                                                                                          
plasma-scriptengine-javascript/quantal plasma-scriptengine-ruby/quantal 
plasma-scriptengine-webkit/quantal plasma-wallpapers-addons/quantal 
plasma-widget-folderview/quantal plasma-widget-kimpanel/quantal 
plasma-widgets-workspace/quantal print-manager/quantal qapt-batch/quantal 
qapt-deb-installer/quantal ruby-kde4/quantal ruby-plasma/quantal 
ruby-qt4/quantal ruby-qt4-webkit/quantal soprano-daemon/quantal 
systemsettings/quantal tasks-icons/quantal

Disabling kubuntu-ppa PPA from 
/etc/apt/sources.list.d/kubuntu-ppa-beta-quantal.list
Updating packages lists
=W: Failed to fetch http://ppa.launchpad.net/jonls/redshift-ppa/ubuntu/dists/quantal/main/source/Sources  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/jonls/redshift-ppa/ubuntu/dists/quantal/main/binary-amd64/Packages  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/jonls/redshift-ppa/ubuntu/dists/quantal/main/binary-i386/Packages  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/ubuntu-clamav/ppa/ubuntu/dists/quantal/main/source/Sources  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/ubuntu-clamav/ppa/ubuntu/dists/quantal/main/binary-amd64/Packages  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/ubuntu-clamav/ppa/ubuntu/dists/quantal/main/binary-i386/Packages  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.
Warning:  apt-get update failed for some reason
Reading package lists... Done
Building dependency tree       
Reading state information... Done
kdevelop-l10n is already the newest version.
kdevelop-l10n set to manually installed.
kdevelop-php-docs-l10n is already the newest version.
kdevelop-php-docs-l10n set to manually installed.
kdevelop-php-l10n is already the newest version.
kdevelop-php-l10n set to manually installed.
Selected version '4:4.4.1-0ubuntu0.1' (Ubuntu:12.10/quantal-updates [all]) for 'kdevelop-l10n'
Selected version '1.4.1-0ubuntu0.1' (Ubuntu:12.10/quantal-updates [all]) for 'kdevelop-php-docs-l10n'
Selected version '1.4.1-0ubuntu0.1' (Ubuntu:12.10/quantal-updates [all]) for 'kdevelop-php-l10n'
Selected version '4:4.9.4-0ubuntu0.1' (Ubuntu:12.10/quantal-updates [amd64]) for 'libsyndication4'
Selected version '4:4.9.4-0ubuntu0.2' (Ubuntu:12.10/quantal-updates [amd64]) for 'libtaskmanager4abi3'
Selected version '4:4.9.4-0ubuntu0.2' (Ubuntu:12.10/quantal-updates [amd64]) for 'libprocesscore4abi1' because of 'libtaskmanager4abi3'
Selected version '4:4.9.4-0ubuntu0.3' (Ubuntu:12.10/quantal-updates [amd64]) for 'libthreadweaver4'
Selected version '4:4.9.4-0ubuntu0.2' (Ubuntu:12.10/quantal-updates [amd64]) for 'libweather-ion6'
Selected version '4:4.9.4-0ubuntu0.1' (Ubuntu:12.10/quantal-updates [all]) for 'marble-data'
Selected version '4:4.9.4-0ubuntu0.1' (Ubuntu:12.10/quantal-updates [amd64]) for 'marble-plugins'
Selected version '4:4.9.4-0ubuntu0.1' (Ubuntu:12.10/quantal-updates [amd64]) for 'nepomuk-core'
Selected version '2.8.0+dfsg.1-0ubuntu1' (Ubuntu:12.10/quantal [amd64]) for 'libsoprano4' because of 'nepomuk-core'
Selected version '2.8.0+dfsg.1-0ubuntu1' (Ubuntu:12.10/quantal [amd64]) for 'soprano-daemon' because of 'libsoprano4'
Selected version '4:4.9.4-0ubuntu0.1' (Ubuntu:12.10/quantal-updates [all]) for 'nepomuk-core-data'
Selected version '4:4.9.4-0ubuntu0.1' (Ubuntu:12.10/quantal-updates [amd64]) for 'nepomuk-core-dev'
Selected version '4:4.9.4-0ubuntu0.1' (Ubuntu:12.10/quantal-updates [amd64]) for 'libnepomukcore4abi1' because of 'nepomuk-core-dev'
Selected version '4:4.9.4-0ubuntu0.1' (Ubuntu:12.10/quantal-updates [amd64]) for 'libnepomuksync4' because of 'nepomuk-core-dev'
Selected version '4:4.9.4-0ubuntu0.1' (Ubuntu:12.10/quantal-updates [amd64]) for 'okular'
Selected version '4:4.9.4-0ubuntu0.1' (Ubuntu:12.10/quantal-updates [amd64]) for 'okular-extra-backends'
Selected version '4:4.9.4-0ubuntu0.1' (Ubuntu:12.10/quantal-updates [amd64]) for 'libokularcore1abi1' because of 'okular-extra-backends'
Selected version '4:4.9.2-0ubuntu1' (Ubuntu:12.10/quantal [all]) for 'oxygen-icon-theme'
Selected version '4:4.9.4-0ubuntu0.1' (Ubuntu:12.10/quantal-updates [amd64]) for 'plasma-containments-addons'
Selected version '4:4.9.4-0ubuntu0.1' (Ubuntu:12.10/quantal-updates [amd64]) for 'plasma-dataengines-addons'
Selected version '4:4.9.4-0ubuntu0.2' (Ubuntu:12.10/quantal-updates [amd64]) for 'plasma-dataengines-workspace'
Selected version '4:4.9.4-0ubuntu0.2' (Ubuntu:12.10/quantal-updates [amd64]) for 'plasma-desktop'
Selected version '4:4.9.4-0ubuntu0.1' (Ubuntu:12.10/quantal-updates [all]) for 'plasma-desktopthemes-artwork'
Selected version '4:4.9.4-0ubuntu0.1' (Ubuntu:12.10/quantal-updates [amd64]) for 'plasma-runners-addons'
Selected version '4:4.9.4-0ubuntu0.1' (Ubuntu:12.10/quantal-updates [amd64]) for 'plasma-scriptengine-javascript'
Selected version '4:4.9.4-0ubuntu0.2' (Ubuntu:12.10/quantal-updates [all]) for 'plasma-scriptengine-ruby'
Selected version '4:4.9.4-0ubuntu0.2' (Ubuntu:12.10/quantal-updates [amd64]) for 'plasma-scriptengine-webkit'
Selected version '4:4.9.4-0ubuntu0.1' (Ubuntu:12.10/quantal-updates [amd64]) for 'plasma-wallpapers-addons'
Selected version '4:4.9.4-0ubuntu0.1' (Ubuntu:12.10/quantal-updates [amd64]) for 'plasma-widget-folderview'
Selected version '4:4.9.4-0ubuntu0.1' (Ubuntu:12.10/quantal-updates [amd64]) for 'plasma-widget-kimpanel'
Selected version '4:4.9.4-0ubuntu0.2' (Ubuntu:12.10/quantal-updates [amd64]) for 'plasma-widgets-workspace'
Selected version '0.2.0-0ubuntu4' (Ubuntu:12.10/quantal-proposed [amd64]) for 'print-manager'
Selected version '1.4.1-0ubuntu2' (Ubuntu:12.10/quantal [amd64]) for 'qapt-batch'
Selected version '1.4.1-0ubuntu2' (Ubuntu:12.10/quantal [amd64]) for 'qapt-deb-installer'
Selected version '4:4.9.2-0ubuntu2' (Ubuntu:12.10/quantal [amd64]) for 'ruby-kde4'
Selected version '4:4.9.2-0ubuntu2' (Ubuntu:12.10/quantal [amd64]) for 'ruby-plasma'
Selected version '4:4.9.2-0ubuntu1' (Ubuntu:12.10/quantal [amd64]) for 'ruby-qt4'
Selected version '4:4.9.2-0ubuntu1' (Ubuntu:12.10/quantal [amd64]) for 'libqtruby4shared2' because of 'ruby-qt4'
Selected version '4:4.9.2-0ubuntu1' (Ubuntu:12.10/quantal [amd64]) for 'ruby-qt4-webkit'
Selected version '2.8.0+dfsg.1-0ubuntu1' (Ubuntu:12.10/quantal [amd64]) for 'soprano-daemon'
Selected version '4:4.9.4-0ubuntu0.2' (Ubuntu:12.10/quantal-updates [amd64]) for 'systemsettings'
Selected version '4:4.9.4-0ubuntu0.1' (Ubuntu:12.10/quantal-updates [all]) for 'tasks-icons'
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 libsoprano4 : Depends: soprano-daemon (= 2.9.0+dfsg.1-0ubuntu1~ubuntu12.10~ppa1) but 2.8.0+dfsg.1-0ubuntu1 is to be installed
 libtaskmanager4abi3 : Depends: libkactivities6 (>= 4.7.90) but it is not going to be installed
 libweather-ion6 : Depends: libplasma3 (>= 4:4.9.4) but it is not going to be installed
 nepomuk-core-dev : Depends: libnepomukcore4abi1 (= 4:4.9.4-0ubuntu0.1) but 4:4.10.0-0ubuntu2~ubuntu12.04.2~ppa1 is to be installed
                    Depends: libnepomuksync4 (= 4:4.9.4-0ubuntu0.1) but 4:4.9.5-0ubuntu0.1~ubuntu12.04.1~ppa1 is to be installed
 okular : Depends: kde-runtime but it is not going to be installed
 plasma-containments-addons : Depends: libplasma3 (>= 4:4.9.4) but it is not going to be installed
 plasma-dataengines-addons : Depends: libplasma3 (>= 4:4.9.4) but it is not going to be installed
 plasma-dataengines-workspace : Depends: libksgrd4 (= 4:4.9.4-0ubuntu0.2) but 4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1 is to be installed
                                Depends: libkworkspace4abi2 (= 4:4.9.4-0ubuntu0.2) but it is not going to be installed
                                Depends: libplasma-geolocation-interface4 (= 4:4.9.4-0ubuntu0.2) but 4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1 is to be installed
                                Depends: libplasma3 (>= 4:4.9.4) but it is not going to be installed
                                Depends: libsolidcontrol4abi2 (= 4:4.9.4-0ubuntu0.2) but 4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1 is to be installed
                                Recommends: ksysguardd (= 4:4.9.4-0ubuntu0.2) but 4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1 is to be installed
 plasma-desktop : Depends: kde-runtime but it is not going to be installed
                  Depends: libkactivities6 (>= 4.7.90) but it is not going to be installed
                  Depends: libkephal4abi1 (= 4:4.9.4-0ubuntu0.2) but 4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1 is to be installed
                  Depends: libkworkspace4abi2 (= 4:4.9.4-0ubuntu0.2) but it is not going to be installed
                  Depends: libplasma3 (>= 4:4.9.4) but it is not going to be installed
                  Depends: libplasmagenericshell4 (= 4:4.9.4-0ubuntu0.2) but it is not going to be installed
                  Depends: libkactivities-bin but it is not going to be installed
                  Recommends: kde-workspace but it is not going to be installed
 plasma-runners-addons : Depends: libplasma3 (>= 4:4.9.4) but it is not going to be installed
 plasma-scriptengine-javascript : Depends: libplasma3 (>= 4:4.9.4) but it is not going to be installed
 plasma-scriptengine-webkit : Depends: libplasma3 (>= 4:4.9.4) but it is not going to be installed
 plasma-wallpapers-addons : Depends: libplasma3 (>= 4:4.9.4) but it is not going to be installed
 plasma-widget-folderview : Depends: libplasma3 (>= 4:4.9.4) but it is not going to be installed
 plasma-widget-kimpanel : Depends: libplasma3 (>= 4:4.9.4) but it is not going to be installed
 plasma-widgets-workspace : Depends: libplasma3 (>= 4:4.9.4) but it is not going to be installed
                            Depends: libplasmaclock4abi3 (= 4:4.9.4-0ubuntu0.2) but it is not going to be installed
 print-manager : Depends: kde-runtime but it is not going to be installed
                 Depends: libplasma3 (>= 4:4.4.4-2~) but it is not going to be installed
 qapt-batch : Depends: kde-runtime but it is not going to be installed
 qapt-deb-installer : Depends: kde-runtime but it is not going to be installed
 ruby-plasma : Depends: libsmokeplasma3 (>= 4:4.9.2) but it is not going to be installed
 systemsettings : Depends: kde-runtime but it is not going to be installed
                  Depends: libplasma3 (>= 4:4.9.4) but it is not going to be installed
W: Duplicate sources.list entry http://ppa.launchpad.net/libreoffice/ppa/ubuntu/ quantal/main amd64 Packages (/var/lib/apt/lists/ppa.launchpad.net_libreoffice_ppa_ubuntu_dists_quantal_main_binary-amd64_Packages)
W: Duplicate sources.list entry http://ppa.launchpad.net/libreoffice/ppa/ubuntu/ quantal/main i386 Packages (/var/lib/apt/lists/ppa.launchpad.net_libreoffice_ppa_ubuntu_dists_quantal_main_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
/usr/sbin/ppa-purge: line 161: aptitude: command not found
Warning:  Something went wrong, packages may not have been reverted
```

Even worse.  Is there really no easy way to just re-install KDE?

---

### Post by zombifier25 on 2013-02-15
Looks like you still have some leftover 4.10 packages. Have you purged that PPA too?

---

### Post by carl4926 on 2013-02-15
Somewhat of a stab at it
Edit your sources to the default list
Run 
```
sudo apt-get update && dist-upgrade
```

---

### Post by Stonecold1995 on 2013-02-15
> **zombifier25 said:**
> Looks like you still have some leftover 4.10 packages. Have you purged that PPA too?
Yes.

> **carl4926 said:**
> Somewhat of a stab at it
Edit your sources to the default list
Run 
```
sudo apt-get update && dist-upgrade
```
The problem isn't with the sources, it's with the installed dependencies (I tried installing some manually because the backports didn't work, and apparently that screwed it up).

There is a way to install 4.9 without completely formatting and reinstalling the whole OS, right?

---

### Post by MadmanRB on 2013-02-15
Very strange, my update to KDE4.10 in Ubuntu went fine via the ppa.
Did muon software center have issues of some kind?

---

### Post by carl4926 on 2013-02-15
But a dist-upgrade should force everything back to square one.

But quite honestly, if this were mine, I'd be considering a clean install...considering!

I asked you to test a new user for a reason. As kde settings are known for getting borked. A new user often reveals that all is well with the system, and that it's just a messed up .kde

---

### Post by MadmanRB on 2013-02-15
> **carl4926 said:**
> But a dist-upgrade should force everything back to square one.

But quite honestly, if this were mine, I'd be considering a clean install...considering!

I asked you to test a new user for a reason. As kde settings are known for getting borked. A new user often reveals that all is well with the system, and that it's just a messed up .kde

Yes though I have noticed vast improvements in moving from one kde to another.
It actually did better in the last three updates of this kind then unity did in its last three.

---

### Post by carl4926 on 2013-02-15
> **MadmanRB said:**
> Yes though I have noticed vast improvements in moving from one kde to another.
It actually did better in the last three updates of this kind then unity did in its last three.

I agree              .

---

### Post by Stonecold1995 on 2013-02-15
> **MadmanRB said:**
> Very strange, my update to KDE4.10 in Ubuntu went fine via the ppa.
Did muon software center have issues of some kind?
I didn't use Muon to upgrade.  And actually, upgrading required me to remove kubuntu-desktop and muon so each package could be installed by itself (but I can't install kubuntu-desktop, nor can I re-install it because it's not installed).  To install it, it requires plasma-netbook, but plasma-netbook has several dependencies that are too "new" for it, and stupid apt-get is refusing to download an older version than what is currently installed.

> **carl4926 said:**
> But a dist-upgrade should force everything back to square one.

But quite honestly, if this were mine, I'd be considering a clean install...considering!

I asked you to test a new user for a reason. As kde settings are known  for getting borked. A new user often reveals that all is well with the  system, and that it's just a messed up .kde
Ah, I see.  Yeah, I did that and KDE looked a LOT different, but some of the widgets were still malfunctioning.  Also, dist-upgrade refuses to set things back to square one, it says everything is fine but it clearly isn't.

I think all that needs to be done now is kubuntu-desktop must be installed (I once messed with KDE before and I fixed it by re-installing kubuntu-desktop), here's what's happening:
```
alex@kubuntu:~$ sudo apt-get install kubuntu-desktop
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 kubuntu-desktop : Depends: plasma-netbook but it is not going to be installed
                   Recommends: akregator but it is not going to be installed
                   Recommends: kaddressbook but it is not going to be installed
                   Recommends: kmail but it is not going to be installed
                   Recommends: kontact but it is not going to be installed
                   Recommends: korganizer but it is not going to be installed
                   Recommends: plasma-widgets-addons but it is not going to be installed                                                                                                
E: Unable to correct problems, you have held broken packages.                                                                                                                           
alex@kubuntu:~$ sudo apt-get install plasma-netbook
Reading package lists... Done                                                                                                                                                           
Building dependency tree                                                                                                                                                                
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 plasma-netbook : Depends: libkephal4abi1 (= 4:4.9.5-0ubuntu0.1~ubuntu12.10~ppa2) but 4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1 is to be installed
                  Depends: libplasmagenericshell4 (= 4:4.9.5-0ubuntu0.1~ubuntu12.10~ppa2) but 4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1 is to be installed
                  Depends: plasma-widgets-workspace (= 4:4.9.5-0ubuntu0.1~ubuntu12.10~ppa2) but 4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1 is to be installed
E: Unable to correct problems, you have held broken packages.
alex@kubuntu:~$ sudo dpkg --list | grep -E "plasma-widgets-workspace|libplasmagenericshell4|libkephal4abi1"
ii  libkephal4abi1                                              4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        API for easier handling of multihead systems
ii  libplasmagenericshell4                                      4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        shared elements for all the plasma shells
ii  plasma-widgets-workspace                                    4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        plasma widgets and containments for the KDE Plasma Workspace
alex@kubuntu:~$ sudo apt-get install --reinstall plasma-widgets-workspace libplasmagenericshell4 libkephal4abi1
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reinstallation of libkephal4abi1 is not possible, it cannot be downloaded.
Reinstallation of plasma-widgets-workspace is not possible, it cannot be downloaded.
Reinstallation of libplasmagenericshell4 is not possible, it cannot be downloaded.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```The PPA that I'm using (no longer the beta or backports version) calls for an older version of plasma-widgets-workspace, but apt-get doesn't want to download an older version.

---

### Post by Stonecold1995 on 2013-02-15
I must have REALLY screwed everything up.  I tried manually downloading some of the .deb files for the older version to install, and they seemed to install, but for ever dependency I fixed, a huge amount of unmet ones were added, so now trying to install plasma-notebook (which is required for kubuntu-desktop to install) causes THIS horrible dependency hell:

```
alex@kubuntu:~$ sudo apt-get install kubuntu-desktop
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 kde-window-manager-common : Depends: libkworkspace4abi2 (= 4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1) but 4:4.9.5-0ubuntu0.1~ubuntu12.10~ppa2 is to be installed
 kde-workspace-bin : Depends: libkworkspace4abi2 (= 4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1) but 4:4.9.5-0ubuntu0.1~ubuntu12.10~ppa2 is to be installed
                     Depends: libplasmagenericshell4 (= 4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1) but 4:4.9.5-0ubuntu0.1~ubuntu12.10~ppa2 is to be installed
 kde-workspace-dev : Depends: libkephal4abi1 (= 4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1) but 4:4.9.5-0ubuntu0.1~ubuntu12.10~ppa2 is to be installed
                     Depends: libkworkspace4abi2 (= 4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1) but 4:4.9.5-0ubuntu0.1~ubuntu12.10~ppa2 is to be installed
                     Depends: libplasmaclock4abi3 (= 4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1) but 4:4.9.5-0ubuntu0.1~ubuntu12.10~ppa2 is to be installed
                     Depends: libplasmagenericshell4 (= 4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1) but 4:4.9.5-0ubuntu0.1~ubuntu12.10~ppa2 is to be installed
 kdm : Depends: libkworkspace4abi2 (= 4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1) but 4:4.9.5-0ubuntu0.1~ubuntu12.10~ppa2 is to be installed
 kubuntu-desktop : Depends: plasma-netbook but it is not going to be installed
                   Depends: software-properties-kde but it is not going to be installed
                   Recommends: akonadi-facebook but it is not going to be installed
                   Recommends: akregator but it is not going to be installed
                   Recommends: amarok but it is not going to be installed
                   Recommends: apport-kde but it is not going to be installed
                   Recommends: apturl-kde but it is not going to be installed
                   Recommends: bluedevil but it is not going to be installed
                   Recommends: dragonplayer but it is not going to be installed
                   Recommends: jockey-kde but it is not going to be installed
                   Recommends: kaddressbook but it is not going to be installed
                   Recommends: kde-config-touchpad but it is not going to be installed
                   Recommends: kde-telepathy but it is not going to be installed
                   Recommends: kexi but it is not going to be installed
                   Recommends: kmail but it is not going to be installed
                   Recommends: kontact but it is not going to be installed
                   Recommends: korganizer but it is not going to be installed
                   Recommends: kpat but it is not going to be installed
                   Recommends: kppp but it is not going to be installed
                   Recommends: krdc but it is not going to be installed
                   Recommends: krita but it is not going to be installed
                   Recommends: kubuntu-notification-helper but it is not going to be installed
                   Recommends: muon but it is not going to be installed
                   Recommends: muon-installer but it is not going to be installed
                   Recommends: muon-notifier but it is not going to be installed
                   Recommends: plasma-widget-facebook but it is not going to be installed
                   Recommends: plasma-widgets-addons but it is not going to be installed
                   Recommends: quassel but it is not going to be installed
                   Recommends: rekonq but it is not going to be installed
                   Recommends: usb-creator-kde but it is not going to be installed
                   Recommends: userconfig but it is not going to be installed
 plasma-dataengines-workspace : Depends: libksgrd4 (= 4:4.9.5-0ubuntu0.1~ubuntu12.10~ppa2) but 4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1 is to be installed
                                Depends: libplasma-geolocation-interface4 (= 4:4.9.5-0ubuntu0.1~ubuntu12.10~ppa2) but 4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1 is to be installed
                                Depends: libsolidcontrol4abi2 (= 4:4.9.5-0ubuntu0.1~ubuntu12.10~ppa2) but 4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1 is to be installed
                                Depends: libtaskmanager4abi3 (= 4:4.9.5-0ubuntu0.1~ubuntu12.10~ppa2) but 4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1 is to be installed
                                Depends: libweather-ion6 (= 4:4.9.5-0ubuntu0.1~ubuntu12.10~ppa2) but 4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1 is to be installed
                                Recommends: ksysguardd (= 4:4.9.5-0ubuntu0.1~ubuntu12.10~ppa2) but 4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1 is to be installed
 plasma-desktop : Depends: libkephal4abi1 (= 4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1) but 4:4.9.5-0ubuntu0.1~ubuntu12.10~ppa2 is to be installed
                  Depends: libkworkspace4abi2 (= 4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1) but 4:4.9.5-0ubuntu0.1~ubuntu12.10~ppa2 is to be installed
                  Depends: libplasmagenericshell4 (= 4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1) but 4:4.9.5-0ubuntu0.1~ubuntu12.10~ppa2 is to be installed
                  Depends: plasma-widgets-workspace (= 4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1) but 4:4.9.5-0ubuntu0.1~ubuntu12.10~ppa2 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
```
I ran "sudo apt-get -f install", and that removed kdm and related packages, when I tried to re-install them, this is what I got now:
```
alex@kubuntu:~$ sudo apt-get install kde-window-manager kde-window-manager-active kde-window-manager-active-gles kde-window-manager-common kde-window-manager-gles kde-workspace kde-workspace-bin kde-workspace-dev kdm plasma-dataengines-workspace plasma-desktop plasma-wallpapers-addons plasma-widgets-workspace
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 kde-runtime : Recommends: kubuntu-debug-installer but it is not going to be installed
               Breaks: kde-workspace-bin (< 4:4.9.95) but 4:4.9.5-0ubuntu0.1~ubuntu12.10~ppa2 is to be installed
 kde-window-manager : Depends: libkdecorations4abi1 (= 4:4.9.5-0ubuntu0.1~ubuntu12.10~ppa2) but 4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1 is to be installed
                      Depends: libkwineffects1abi4 (= 4:4.9.5-0ubuntu0.1~ubuntu12.10~ppa2) but 4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1 is to be installed
                      Depends: libkwinglutils1abi1 (= 4:4.9.5-0ubuntu0.1~ubuntu12.10~ppa2) but 4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1 is to be installed
                      Depends: libkwinnvidiahack4 (= 4:4.9.5-0ubuntu0.1~ubuntu12.10~ppa2) but 4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1 is to be installed
 kde-window-manager-active : Depends: libkdecorations4abi1 (= 4:4.9.5-0ubuntu0.1~ubuntu12.10~ppa2) but 4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1 is to be installed
                             Depends: libkwinactiveeffects1abi4 (= 4:4.9.5-0ubuntu0.1~ubuntu12.10~ppa2) but 4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1 is to be installed
                             Depends: libkwinactiveglutils1abi1 (= 4:4.9.5-0ubuntu0.1~ubuntu12.10~ppa2) but 4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1 is to be installed
                             Depends: libkwinactivenvidiahack4 (= 4:4.9.5-0ubuntu0.1~ubuntu12.10~ppa2) but 4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1 is to be installed
 kde-window-manager-active-gles : Depends: libkdecorations4abi1 (= 4:4.9.5-0ubuntu0.1~ubuntu12.10~ppa2) but 4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1 is to be installed
                                  Depends: libkwinactiveeffects1abi4 (= 4:4.9.5-0ubuntu0.1~ubuntu12.10~ppa2) but 4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1 is to be installed
                                  Depends: libkwinactiveglesutils1 (= 4:4.9.5-0ubuntu0.1~ubuntu12.10~ppa2) but 4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1 is to be installed
                                  Depends: libkwinactivenvidiahack4 (= 4:4.9.5-0ubuntu0.1~ubuntu12.10~ppa2) but 4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1 is to be installed
 kde-window-manager-common : Depends: libkdecorations4abi1 (= 4:4.9.5-0ubuntu0.1~ubuntu12.10~ppa2) but 4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1 is to be installed
                             Depends: libkwineffects1abi4 (= 4:4.9.5-0ubuntu0.1~ubuntu12.10~ppa2) but 4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1 is to be installed
 kde-window-manager-gles : Depends: libkdecorations4abi1 (= 4:4.9.5-0ubuntu0.1~ubuntu12.10~ppa2) but 4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1 is to be installed
                           Depends: libkwineffects1abi4 (= 4:4.9.5-0ubuntu0.1~ubuntu12.10~ppa2) but 4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1 is to be installed
                           Depends: libkwinglesutils1 (= 4:4.9.5-0ubuntu0.1~ubuntu12.10~ppa2) but 4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1 is to be installed
                           Depends: libkwinnvidiahack4 (= 4:4.9.5-0ubuntu0.1~ubuntu12.10~ppa2) but 4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1 is to be installed
 kde-workspace-bin : Depends: libkscreensaver5 (= 4:4.9.5-0ubuntu0.1~ubuntu12.10~ppa2) but 4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1 is to be installed
                     Depends: libprocesscore4abi1 (= 4:4.9.5-0ubuntu0.1~ubuntu12.10~ppa2) but 4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1 is to be installed
                     Depends: libprocessui4a (= 4:4.9.5-0ubuntu0.1~ubuntu12.10~ppa2) but 4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1 is to be installed
                     Depends: libsolidcontrol4abi2 (= 4:4.9.5-0ubuntu0.1~ubuntu12.10~ppa2) but 4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1 is to be installed
                     Depends: libsolidcontrolifaces4abi2 (= 4:4.9.5-0ubuntu0.1~ubuntu12.10~ppa2) but 4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1 is to be installed
                     Depends: kde-workspace-data (= 4:4.9.5-0ubuntu0.1~ubuntu12.10~ppa2) but 4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1 is to be installed
                     Depends: kde-workspace-kgreet-plugins (= 4:4.9.5-0ubuntu0.1~ubuntu12.10~ppa2) but 4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1 is to be installed
 kde-workspace-dev : Depends: libksignalplotter4 (= 4:4.9.5-0ubuntu0.1~ubuntu12.10~ppa2) but 4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1 is to be installed
                     Depends: liblsofui4 (= 4:4.9.5-0ubuntu0.1~ubuntu12.10~ppa2) but 4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1 is to be installed
                     Depends: libprocessui4a (= 4:4.9.5-0ubuntu0.1~ubuntu12.10~ppa2) but 4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1 is to be installed
                     Depends: libkdecorations4abi1 (= 4:4.9.5-0ubuntu0.1~ubuntu12.10~ppa2) but 4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1 is to be installed
                     Depends: libkwinglesutils1 (= 4:4.9.5-0ubuntu0.1~ubuntu12.10~ppa2) but 4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1 is to be installed
                     Depends: libkwinactiveglutils1abi1 (= 4:4.9.5-0ubuntu0.1~ubuntu12.10~ppa2) but 4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1 is to be installed
                     Depends: libkwinactiveglesutils1 (= 4:4.9.5-0ubuntu0.1~ubuntu12.10~ppa2) but 4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1 is to be installed
                     Depends: libkwineffects1abi4 (= 4:4.9.5-0ubuntu0.1~ubuntu12.10~ppa2) but 4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1 is to be installed
                     Depends: libkwinactiveeffects1abi4 (= 4:4.9.5-0ubuntu0.1~ubuntu12.10~ppa2) but 4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1 is to be installed
                     Depends: libkwinnvidiahack4 (= 4:4.9.5-0ubuntu0.1~ubuntu12.10~ppa2) but 4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1 is to be installed
                     Depends: libkwinactivenvidiahack4 (= 4:4.9.5-0ubuntu0.1~ubuntu12.10~ppa2) but 4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1 is to be installed
                     Depends: libkscreensaver5 (= 4:4.9.5-0ubuntu0.1~ubuntu12.10~ppa2) but 4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1 is to be installed
                     Depends: libksgrd4 (= 4:4.9.5-0ubuntu0.1~ubuntu12.10~ppa2) but 4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1 is to be installed
                     Depends: libplasma-geolocation-interface4 (= 4:4.9.5-0ubuntu0.1~ubuntu12.10~ppa2) but 4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1 is to be installed
                     Depends: libkwinglutils1abi1 (= 4:4.9.5-0ubuntu0.1~ubuntu12.10~ppa2) but 4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1 is to be installed
                     Depends: libprocesscore4abi1 (= 4:4.9.5-0ubuntu0.1~ubuntu12.10~ppa2) but 4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1 is to be installed
                     Depends: libsolidcontrol4abi2 (= 4:4.9.5-0ubuntu0.1~ubuntu12.10~ppa2) but 4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1 is to be installed
                     Depends: libsolidcontrolifaces4abi2 (= 4:4.9.5-0ubuntu0.1~ubuntu12.10~ppa2) but 4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1 is to be installed
                     Depends: libtaskmanager4abi3 (= 4:4.9.5-0ubuntu0.1~ubuntu12.10~ppa2) but 4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1 is to be installed
                     Depends: libweather-ion6 (= 4:4.9.5-0ubuntu0.1~ubuntu12.10~ppa2) but 4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1 is to be installed
 kdm : Depends: kde-workspace-kgreet-plugins (= 4:4.9.5-0ubuntu0.1~ubuntu12.10~ppa2) but 4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1 is to be installed
 plasma-dataengines-workspace : Depends: libksgrd4 (= 4:4.9.5-0ubuntu0.1~ubuntu12.10~ppa2) but 4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1 is to be installed
                                Depends: libplasma-geolocation-interface4 (= 4:4.9.5-0ubuntu0.1~ubuntu12.10~ppa2) but 4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1 is to be installed
                                Depends: libsolidcontrol4abi2 (= 4:4.9.5-0ubuntu0.1~ubuntu12.10~ppa2) but 4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1 is to be installed
                                Depends: libtaskmanager4abi3 (= 4:4.9.5-0ubuntu0.1~ubuntu12.10~ppa2) but 4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1 is to be installed
                                Depends: libweather-ion6 (= 4:4.9.5-0ubuntu0.1~ubuntu12.10~ppa2) but 4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1 is to be installed
                                Recommends: ksysguardd (= 4:4.9.5-0ubuntu0.1~ubuntu12.10~ppa2) but 4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1 is to be installed
 plasma-desktop : Depends: libtaskmanager4abi3 (= 4:4.9.5-0ubuntu0.1~ubuntu12.10~ppa2) but 4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1 is to be installed
 plasma-wallpapers-addons : Depends: plasma-dataengines-addons (= 4:4.9.5-0ubuntu0.1~ubuntu12.10~ppa1) but 4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1 is to be installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
```
apt-get made it even worse!  As soon as I log out, I'm going to lose kdm, and I can't re-install it.  Seriously, there HAS to be some way to force-uninstall everything related to KDE, right?  Something to bypass apt-get's warnings and refusal to reinstall?

If there isn't, I'll probably just re-install.  If a little under a month ago, I made a backup of / (not /home) with dd, would running "sudo dd if=/media/path/to/backup/sdb5.img of=/dev/sdb5" on a live CD work if /home isn't copied as well?  The drive is encrypted with LUKS, what are the dangers that I'd fsck everything up?

Also, I made the backup while everything was on and mounted, does that mean the image I created could be corrupt and that I'd be restoring a useless image?

---

### Post by Stonecold1995 on 2013-02-15
I think these are the packages which I need to downgrade, but that apt-get is refusing to do:
```
alex@kubuntu:~$ sudo dpkg --list | grep 4.10.0
ii  ark                                                         4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        archive utility
ii  ark-dbg                                                     4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        debugging symbols for ark
ii  audiocd-kio                                                 4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        transparent audio CD access for applications using the KDE Platform
ii  dolphin                                                     4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        file manager
ii  freespacenotifier                                           4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        free space notification module for KDE
ii  jovie                                                       4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        text-to-speech system for KDE
ii  kaccessible                                                 4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        accessibility services for Qt applications
ii  kamera                                                      4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        digital camera support for KDE applications
ii  kate                                                        4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        K Advanced Text Editor
ii  kate-data                                                   4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             all          shared data files for kate
ii  kate-dbg                                                    4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        debugging symbols for Kate
ii  katepart                                                    4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        kate KPart
ii  kcalc                                                       4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        simple and scientific calculator
ii  kde-base-artwork                                            4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             all          base artwork for the KDE Plasma Workspace
ii  kde-baseapps-bin                                            4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        core binaries for the KDE base applications
ii  kde-baseapps-data                                           4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             all          shared data files for the KDE base applications
ii  kde-baseapps-dbg                                            4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        debugging symbols for the KDE base applications module
ii  kde-l10n-engb                                               4:4.10.0-0ubuntu1~ubuntu12.04.1~ppa1             all          British English (engb) localization for KDE
ii  kde-l10n-ja                                                 4:4.10.0-0ubuntu1~ubuntu12.04.1~ppa1             all          Japanese (ja) localization for KDE
ii  kde-runtime-data                                            4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             all          shared data files for the KDE base runtime module
ii  kde-style-oxygen                                            4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        Oxygen widget style
ii  kde-wallpapers                                              4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             all          set of wallpapers for the Plasma workspace
ii  kde-wallpapers-default                                      4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             all          default wallpaper for the Plasma workspace
rc  kde-window-manager-common                                   4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        K window manager (KWin) Common Files
rc  kde-workspace-bin                                           4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        core binaries for the KDE Plasma Workspace
ii  kde-workspace-data                                          4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             all          shared data files for the KDE Plasma Workspace
ii  kde-workspace-dbg                                           4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        debugging symbols for the KDE Plasma Workspaces
ii  kde-workspace-kgreet-plugins                                4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        KDE greet libraries for authentication
ii  kde-zeroconf                                                4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        zeroconf plugins and kio slaves for KDE
ii  kdebase-bin                                                 4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             all          Transitional package for new kde-baseapps
ii  kdebase-runtime                                             4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             all          Transitional package for the KDE runtime components
ii  kdegames-card-data                                          4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             all          card decks for KDE games
ii  kdegames-data                                               4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             all          games from the official KDE release -- shared data files
ii  kdegraphics-strigi-analyzer                                 4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        graphics file format plugins for Strigi Desktop Search
ii  kdelibs-bin                                                 4:4.10.0-0ubuntu2~ubuntu12.04.2~ppa1             amd64        core executables for KDE Applications
ii  kdelibs5-data                                               4:4.10.0-0ubuntu2~ubuntu12.04.2~ppa1             all          core shared data for all KDE Applications
ii  kdelibs5-dbg                                                4:4.10.0-0ubuntu2~ubuntu12.04.2~ppa1             amd64        debugging symbols for the KDE Development Platform libraries
ii  kdelibs5-dev                                                4:4.10.0-0ubuntu2~ubuntu12.04.2~ppa1             amd64        development files for the KDE Development Platform libraries
ii  kdelibs5-plugins                                            4:4.10.0-0ubuntu2~ubuntu12.04.2~ppa1             amd64        core plugins for KDE Applications
ii  kdenetwork-filesharing                                      4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        network filesharing configuration module
ii  kdepasswd                                                   4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        graphical password changing utility
ii  kdepim-kresources                                           4:4.10.0a-0ubuntu1~ubuntu12.04.2~ppa1            amd64        KDE PIM resource plugins
ii  kdepim-runtime                                              4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        Runtime components for akonadi-kde
ii  kdepim-strigi-plugins                                       4:4.10.0a-0ubuntu1~ubuntu12.04.2~ppa1            amd64        PIM file format plugins for Strigi Desktop Search
ii  kdepimlibs-kio-plugins                                      4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        kio slaves used by KDE PIM applications
ii  kdepimlibs5-dev                                             4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        development files for the KDE Development Platform PIM libraries
rc  kdm                                                         4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        KDE Display Manager for X11
ii  kdoctools                                                   4:4.10.0-0ubuntu2~ubuntu12.04.2~ppa1             amd64        various tools for accessing application documentation
ii  khelpcenter4                                                4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        help center
ii  kinfocenter                                                 4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        system information viewer
ii  klipper                                                     4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        clipboard manager
ii  kmag                                                        4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        screen magnifier tool
ii  kmenuedit                                                   4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        XDG menu editor
ii  kmix                                                        4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        volume control and mixer
ii  kmousetool                                                  4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        mouse manipulation tool for the disabled
ii  kmouth                                                      4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        type-and-say frontend for speech synthesizers
ii  knotes                                                      4:4.10.0a-0ubuntu1~ubuntu12.04.2~ppa1            amd64        sticky notes application
ii  konsole                                                     4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        X terminal emulator
ii  konsole-dbg                                                 4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        debugging symbols for the KDE X terminal emulator
ii  krosspython                                                 4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        Python module for Kross
ii  kruler                                                      4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        screen ruler
ii  ksysguard                                                   4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        process monitor and system statistics
ii  ksysguardd                                                  4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        System Guard Daemon
ii  ksystemlog                                                  4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        system log viewer
ii  kwalletmanager                                              4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        secure password wallet manager
ii  libakonadi-calendar4                                        4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        library providing calendar helpers for Akonadi items
ii  libakonadi-contact4                                         4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        library for using the Akonadi PIM data server
ii  libakonadi-kabc4                                            4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        library for using the Akonadi PIM data server
ii  libakonadi-kcal4                                            4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        library for using the Akonadi PIM data server
ii  libakonadi-kde4                                             4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        library for using the Akonadi PIM data server
ii  libakonadi-kmime4                                           4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        library for using the Akonadi PIM data server
ii  libakonadi-notes4                                           4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        library providing notes helpers for Akonadi items
ii  libakonadi-socialutils4                                     4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        Akonadi resources for handling social feeds
ii  libaudiocdplugins4                                          4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        transparent audio CD access for applications using the KDE Platform
ii  libfreetype6:amd64                                          2.4.10-0ubuntu1.1                                amd64        FreeType 2 font engine, shared library files
ii  libfreetype6:i386                                           2.4.10-0ubuntu1.1                                i386         FreeType 2 font engine, shared library files
ii  libfreetype6-dev                                            2.4.10-0ubuntu1.1                                amd64        FreeType 2 font engine, development files
ii  libgpgme++2                                                 4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        c++ wrapper library for gpgme
ii  libkabc4                                                    4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        library for handling address book data
ii  libkactivities-bin                                          4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        executables for the KDE Activities
ii  libkactivities-dev                                          4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        development files for the KDE Activities libraries
ii  libkactivities-models1                                      4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        Activities models library
ii  libkactivities6                                             4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        Activities library
ii  libkalarmcal2                                               4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        library for handling kalarm calendar data
ii  libkateinterfaces4                                          4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        kate plugin interface library
ii  libkatepartinterfaces4                                      4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        kate part library
ii  libkblog4                                                   4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        client-side support library for web application remote blogging APIs
ii  libkcal4                                                    4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        library for handling calendar data
ii  libkcalcore4                                                4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        library for handling calendar data
ii  libkcalutils4                                               4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        library with utility functions for the handling of calendar data
ii  libkcddb4                                                   4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        CDDB library for KDE Platform (runtime)
ii  libkcmutils4                                                4:4.10.0-0ubuntu2~ubuntu12.04.2~ppa1             amd64        utility classes for using KCM modules
ii  libkcompactdisc4                                            4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        KDE library for interfacing with CDs
ii  libkde3support4                                             4:4.10.0-0ubuntu2~ubuntu12.04.2~ppa1             amd64        KDE 3 Support Library for the KDE 4 Platform
ii  libkdeclarative5                                            4:4.10.0-0ubuntu2~ubuntu12.04.2~ppa1             amd64        declarative library for plasma
ii  libkdecorations4abi1                                        4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        library used by decorations for the KDE window manager
ii  libkdecore5                                                 4:4.10.0-0ubuntu2~ubuntu12.04.2~ppa1             amd64        KDE Platform Core Library
ii  libkdepim4                                                  4:4.10.0a-0ubuntu1~ubuntu12.04.2~ppa1            amd64        KDE PIM library
ii  libkdesu5                                                   4:4.10.0-0ubuntu2~ubuntu12.04.2~ppa1             amd64        Console-mode Authentication Library for the KDE Platform
ii  libkdeui5                                                   4:4.10.0-0ubuntu2~ubuntu12.04.2~ppa1             amd64        KDE Platform User Interface Library
ii  libkdewebkit5                                               4:4.10.0-0ubuntu2~ubuntu12.04.2~ppa1             amd64        KDE WebKit Library
ii  libkdnssd4                                                  4:4.10.0-0ubuntu2~ubuntu12.04.2~ppa1             amd64        DNS-SD Protocol Library for the KDE Platform
ii  libkemoticons4                                              4:4.10.0-0ubuntu2~ubuntu12.04.2~ppa1             amd64        utility classes to deal with emoticon themes
ii  libkexiv2-data                                              4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             all          Qt-like interface for the libexiv2 library -- data files
ii  libkfile4                                                   4:4.10.0-0ubuntu2~ubuntu12.04.2~ppa1             amd64        File Selection Dialog Library for KDE Platform
ii  libkholidays4                                               4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        holidays calculation library
ii  libkhtml5                                                   4:4.10.0-0ubuntu2~ubuntu12.04.2~ppa1             amd64        KHTML Web Content Rendering Engine
ii  libkidletime4                                               4:4.10.0-0ubuntu2~ubuntu12.04.2~ppa1             amd64        library to provide information about idle time
ii  libkimap4                                                   4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        library for handling IMAP data
ii  libkimproxy4                                                4:4.10.0-0ubuntu2~ubuntu12.04.2~ppa1             amd64        Instant Messaging Interface Library for the KDE Platform
ii  libkio5                                                     4:4.10.0-0ubuntu2~ubuntu12.04.2~ppa1             amd64        Network-enabled File Management Library for the KDE Platform
ii  libkipi-data                                                4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             all          data files for kipi libraries
ii  libkjsapi4                                                  4:4.10.0-0ubuntu2~ubuntu12.04.2~ppa1             amd64        KJS API Library for the KDE Development Platform
ii  libkjsembed4                                                4:4.10.0-0ubuntu2~ubuntu12.04.2~ppa1             amd64        library for binding JavaScript objects to QObjects
ii  libkldap4                                                   4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        library for accessing LDAP
ii  libkmbox4                                                   4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        library for handling mbox mailboxes
ii  libkmediaplayer4                                            4:4.10.0-0ubuntu2~ubuntu12.04.2~ppa1             amd64        KMediaPlayer Interface for the KDE Platform
ii  libkmime4                                                   4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        library for handling MIME data
ii  libknewstuff2-4                                             4:4.10.0-0ubuntu2~ubuntu12.04.2~ppa1             amd64        "Get Hot New Stuff" v2 Library for the KDE Platform
ii  libknewstuff3-4                                             4:4.10.0-0ubuntu2~ubuntu12.04.2~ppa1             amd64        "Get Hot New Stuff" v3 Library for the KDE Platform
ii  libknotifyconfig4                                           4:4.10.0-0ubuntu2~ubuntu12.04.2~ppa1             amd64        library for configuring KDE Notifications
ii  libkntlm4                                                   4:4.10.0-0ubuntu2~ubuntu12.04.2~ppa1             amd64        NTLM Authentication Library for the KDE Platform
ii  libkonq-common                                              4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        core Konqueror library - support files
ii  libkonq5-dev                                                4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        development files for the Konqueror libraries
ii  libkonq5-templates                                          4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             all          data files for the Konqueror libraries
ii  libkonq5abi1                                                4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        core libraries for Konqueror
ii  libkonqsidebarplugin-dev                                    4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        konqueror sidebar plugin library development files
ii  libkonqsidebarplugin4a                                      4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        konqueror sidebar plugin library
ii  libkontactinterface4                                        4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        Kontact interface library
ii  libkparts4                                                  4:4.10.0-0ubuntu2~ubuntu12.04.2~ppa1             amd64        Framework for the KDE Platform Graphical Components
ii  libkpimidentities4                                          4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        library for managing user identities
ii  libkpimtextedit4                                            4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        library that provides a textedit with PIM-specific features
ii  libkpimutils4                                               4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        library for dealing with email addresses
ii  libkprintutils4                                             4:4.10.0-0ubuntu2~ubuntu12.04.2~ppa1             amd64        utility classes to deal with printing
ii  libkpty4                                                    4:4.10.0-0ubuntu2~ubuntu12.04.2~ppa1             amd64        Pseudo Terminal Library for the KDE Platform
ii  libkresources4                                              4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        KDE Resource framework library
ii  libkrosscore4                                               4:4.10.0-0ubuntu2~ubuntu12.04.2~ppa1             amd64        Kross Core Library
ii  libkrossui4                                                 4:4.10.0-0ubuntu2~ubuntu12.04.2~ppa1             amd64        Kross UI Library
ii  libksane-data                                               4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             all          scanner library (data files)
ii  libksane0                                                   4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        scanner library (runtime)
ii  libkscreensaver5                                            4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        library of the KDE Screensaver system
ii  libksgrd4                                                   4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        library for ksysguard
ii  libksignalplotter4                                          4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        KSignalPlotter widget
ii  libktexteditor4                                             4:4.10.0-0ubuntu2~ubuntu12.04.2~ppa1             amd64        KTextEditor interfaces for the KDE Platform
ii  libktnef4                                                   4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        library for handling TNEF data
ii  libkunitconversion4                                         4:4.10.0-0ubuntu2~ubuntu12.04.2~ppa1             amd64        Unit Conversion library for the KDE Platform
ii  libkutils4                                                  4:4.10.0-0ubuntu2~ubuntu12.04.2~ppa1             amd64        dummy transitional library
ii  libkwinactiveeffects1abi4                                   4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        library used by effects for the KDE window manager Active
ii  libkwinactiveglesutils1                                     4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        library used by accelleration for the KDE window manager Active
ii  libkwinactiveglutils1abi1                                   4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        library used by accellaration for the KDE window manager Active
ii  libkwinactivenvidiahack4                                    4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        library used by nvidia cards for the KDE window manager
ii  libkwineffects1abi4                                         4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        library used by effects for the KDE window manager
ii  libkwinglesutils1                                           4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        library used by accellaration for the KDE window manager
ii  libkwinglutils1abi1                                         4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        library used by accellaration for the KDE window manager
ii  libkwinnvidiahack4                                          4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        library used by nvidia cards for the KDE window manager
ii  libkxmlrpcclient4                                           4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        simple XML-RPC client library
ii  liblsofui4                                                  4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        library for ksysguard based priority scheduling
ii  libmailtransport4                                           4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        mail transport service library
ii  libmarblewidget15                                           4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        Marble globe widget library
ii  libmicroblog4                                               4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        library for using the Microblog Akonadi Resource
ii  libnepomuk4                                                 4:4.10.0-0ubuntu2~ubuntu12.04.2~ppa1             amd64        Nepomuk Meta Data Library
ii  libnepomukcore4abi1                                         4:4.10.0-0ubuntu2~ubuntu12.04.2~ppa1             amd64        The Nepomuk Meta Data Library
ii  libnepomukquery4a                                           4:4.10.0-0ubuntu2~ubuntu12.04.2~ppa1             amd64        Nepomuk Query Library for the KDE Platform
ii  libnepomukutils4                                            4:4.10.0-0ubuntu2~ubuntu12.04.2~ppa1             amd64        Nepomuk Utility Library
ii  libnepomukwidgets4                                          4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        The Nepomuk Semantik Desktop widgets library
ii  libokularcore2abi1                                          4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        libraries for the Okular document viewer
ii  libplasma-geolocation-interface4                            4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        library for the Plasma geolocation
ii  libplasma3                                                  4:4.10.0-0ubuntu2~ubuntu12.04.2~ppa1             amd64        Plasma Library for the KDE Platform
ii  libprocesscore4abi1                                         4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        library for ksysguard based process view
ii  libprocessui4a                                              4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        library for ksysguard process user interface
ii  libqgpgme1                                                  4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        library for GpgME++ integration with Qt
ii  libqtruby4shared2                                           4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        internal library for Qt 4 Ruby bindings
ii  librpm3                                                     4.10.0-4ubuntu0.1                                amd64        RPM shared library
ii  librpmbuild3                                                4.10.0-4ubuntu0.1                                amd64        RPM build shared library
ii  librpmio3                                                   4.10.0-4ubuntu0.1                                amd64        RPM IO shared library
ii  librpmsign1                                                 4.10.0-4ubuntu0.1                                amd64        RPM signing shared library
ii  libsmokebase3                                               4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        SMOKE base library
ii  libsmokekdecore4-3                                          4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        KDE Core SMOKE libraries
ii  libsmokekdeui4-3                                            4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        KDE Ui SMOKE libraries
ii  libsmokekfile3                                              4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        KFile SMOKE library
ii  libsmokekhtml3                                              4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        KHTML SMOKE library
ii  libsmokekio3                                                4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        KIO SMOKE library
ii  libsmokeknewstuff2-3                                        4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        KNewStuff2 SMOKE library
ii  libsmokeknewstuff3-3                                        4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        KNewStuff3 SMOKE library
ii  libsmokekparts3                                             4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        KParts SMOKE libraries
ii  libsmokektexteditor3                                        4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        KTextEditor SMOKE libraries
ii  libsmokekutils3                                             4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        KUtils SMOKE libraries
ii  libsmokenepomuk3                                            4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        Nepomuk SMOKE libraries
ii  libsmokeplasma3                                             4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        Plasma SMOKE library
ii  libsmokeqtcore4-3                                           4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        Qt Core SMOKE library
ii  libsmokeqtdbus4-3                                           4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        Qt D-Bus SMOKE library
ii  libsmokeqtgui4-3                                            4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        Qt Gui SMOKE library
ii  libsmokeqtnetwork4-3                                        4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        Qt Network SMOKE library
ii  libsmokeqtopengl4-3                                         4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        Qt OpenGL SMOKE library
ii  libsmokeqtsql4-3                                            4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        Qt Sql SMOKE library
ii  libsmokeqtsvg4-3                                            4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        Qt Svg SMOKE library
ii  libsmokeqtwebkit4-3                                         4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        Qt WebKit SMOKE library
ii  libsmokeqtxml4-3                                            4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        Qt Xml SMOKE library
ii  libsmokesolid3                                              4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        Solid SMOKE libraries
ii  libsolid4                                                   4:4.10.0-0ubuntu2~ubuntu12.04.2~ppa1             amd64        Solid Library for KDE Platform
ii  libsolidcontrol4abi2                                        4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        library for Solid based network management
ii  libsolidcontrolifaces4abi2                                  4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        library for Solid based network interface management
ii  libsyndication4                                             4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        parser library for RSS and Atom feeds
ii  libtaskmanager4abi3                                         4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        library which provides task management facilities
ii  libthreadweaver4                                            4:4.10.0-0ubuntu2~ubuntu12.04.2~ppa1             amd64        ThreadWeaver Library for the KDE Platform
ii  libweather-ion6                                             4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        library which provides an interface for weather information services
ii  marble-data                                                 4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             all          data files for Marble
ii  marble-plugins                                              4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        plugins for Marble
ii  nepomuk-core-data                                           4:4.10.0-0ubuntu2~ubuntu12.04.2~ppa1             all          Nepomuk Semantik Desktop core libraries -- shared data files
ii  nepomuk-core-dev                                            4:4.10.0-0ubuntu2~ubuntu12.04.2~ppa1             amd64        Nepomuk Semantik Desktop core libraries -- development files
ii  okular-extra-backends                                       4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        additional document format support for Okular
ii  oxygen-icon-theme                                           4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             all          Oxygen icon theme
ii  plasma-containments-addons                                  4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        additional containment plugins for Plasma
ii  plasma-dataengines-addons                                   4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        additional data engines for Plasma
ii  plasma-desktopthemes-artwork                                4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             all          desktop themes for KDE Plasma Workspaces
ii  plasma-runners-addons                                       4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        additional runners for Plasma and Krunner
ii  plasma-scriptengine-ruby                                    4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             all          Ruby script engine for Plasma
ii  plasma-scriptengine-webkit                                  4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        Web and Mac OS X dashboard widget support for Plasma
ii  plasma-widget-folderview                                    4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        plasma widget showing the content of a folder
ii  plasma-widget-kimpanel                                      4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        KIMPanel widget for Plasma
ii  print-manager                                               4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        printer config and monitor tool
ii  rpm                                                         4.10.0-4ubuntu0.1                                amd64        package manager for RPM
ii  rpm-common                                                  4.10.0-4ubuntu0.1                                amd64        common files for RPM
ii  rpm2cpio                                                    4.10.0-4ubuntu0.1                                amd64        tool to convert RPM package to CPIO archive
ii  ruby-kde4                                                   4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        KDE bindings for the Ruby language
ii  ruby-plasma                                                 4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        Plasma Ruby bindings
ii  ruby-qt4                                                    4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        Qt 4 bindings for the Ruby language
ii  ruby-qt4-webkit                                             4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        QtWebKit bindings for the Ruby language
ii  systemsettings                                              4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        System Settings
ii  tasks-icons                                                 4:4.10.0a-0ubuntu1~ubuntu12.04.2~ppa1            all          icon files for the taks management
```

Is there a way to batch-download or downgrade all of these?

---

### Post by Stonecold1995 on 2013-02-15
> **Stonecold1995 said:**
> I think these are the packages which I need to downgrade, but that apt-get is refusing to do:
```
alex@kubuntu:~$ sudo dpkg --list | grep 4.10.0
ii  ark                                                         4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        archive utility
ii  ark-dbg                                                     4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        debugging symbols for ark
ii  audiocd-kio                                                 4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        transparent audio CD access for applications using the KDE Platform
ii  dolphin                                                     4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        file manager
ii  freespacenotifier                                           4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        free space notification module for KDE
ii  jovie                                                       4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        text-to-speech system for KDE
ii  kaccessible                                                 4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        accessibility services for Qt applications
ii  kamera                                                      4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        digital camera support for KDE applications
ii  kate                                                        4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        K Advanced Text Editor
ii  kate-data                                                   4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             all          shared data files for kate
ii  kate-dbg                                                    4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        debugging symbols for Kate
ii  katepart                                                    4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        kate KPart
ii  kcalc                                                       4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        simple and scientific calculator
ii  kde-base-artwork                                            4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             all          base artwork for the KDE Plasma Workspace
ii  kde-baseapps-bin                                            4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        core binaries for the KDE base applications
ii  kde-baseapps-data                                           4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             all          shared data files for the KDE base applications
ii  kde-baseapps-dbg                                            4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        debugging symbols for the KDE base applications module
ii  kde-l10n-engb                                               4:4.10.0-0ubuntu1~ubuntu12.04.1~ppa1             all          British English (engb) localization for KDE
ii  kde-l10n-ja                                                 4:4.10.0-0ubuntu1~ubuntu12.04.1~ppa1             all          Japanese (ja) localization for KDE
ii  kde-runtime-data                                            4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             all          shared data files for the KDE base runtime module
ii  kde-style-oxygen                                            4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        Oxygen widget style
ii  kde-wallpapers                                              4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             all          set of wallpapers for the Plasma workspace
ii  kde-wallpapers-default                                      4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             all          default wallpaper for the Plasma workspace
rc  kde-window-manager-common                                   4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        K window manager (KWin) Common Files
rc  kde-workspace-bin                                           4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        core binaries for the KDE Plasma Workspace
ii  kde-workspace-data                                          4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             all          shared data files for the KDE Plasma Workspace
ii  kde-workspace-dbg                                           4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        debugging symbols for the KDE Plasma Workspaces
ii  kde-workspace-kgreet-plugins                                4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        KDE greet libraries for authentication
ii  kde-zeroconf                                                4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        zeroconf plugins and kio slaves for KDE
ii  kdebase-bin                                                 4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             all          Transitional package for new kde-baseapps
ii  kdebase-runtime                                             4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             all          Transitional package for the KDE runtime components
ii  kdegames-card-data                                          4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             all          card decks for KDE games
ii  kdegames-data                                               4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             all          games from the official KDE release -- shared data files
ii  kdegraphics-strigi-analyzer                                 4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        graphics file format plugins for Strigi Desktop Search
ii  kdelibs-bin                                                 4:4.10.0-0ubuntu2~ubuntu12.04.2~ppa1             amd64        core executables for KDE Applications
ii  kdelibs5-data                                               4:4.10.0-0ubuntu2~ubuntu12.04.2~ppa1             all          core shared data for all KDE Applications
ii  kdelibs5-dbg                                                4:4.10.0-0ubuntu2~ubuntu12.04.2~ppa1             amd64        debugging symbols for the KDE Development Platform libraries
ii  kdelibs5-dev                                                4:4.10.0-0ubuntu2~ubuntu12.04.2~ppa1             amd64        development files for the KDE Development Platform libraries
ii  kdelibs5-plugins                                            4:4.10.0-0ubuntu2~ubuntu12.04.2~ppa1             amd64        core plugins for KDE Applications
ii  kdenetwork-filesharing                                      4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        network filesharing configuration module
ii  kdepasswd                                                   4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        graphical password changing utility
ii  kdepim-kresources                                           4:4.10.0a-0ubuntu1~ubuntu12.04.2~ppa1            amd64        KDE PIM resource plugins
ii  kdepim-runtime                                              4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        Runtime components for akonadi-kde
ii  kdepim-strigi-plugins                                       4:4.10.0a-0ubuntu1~ubuntu12.04.2~ppa1            amd64        PIM file format plugins for Strigi Desktop Search
ii  kdepimlibs-kio-plugins                                      4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        kio slaves used by KDE PIM applications
ii  kdepimlibs5-dev                                             4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        development files for the KDE Development Platform PIM libraries
rc  kdm                                                         4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        KDE Display Manager for X11
ii  kdoctools                                                   4:4.10.0-0ubuntu2~ubuntu12.04.2~ppa1             amd64        various tools for accessing application documentation
ii  khelpcenter4                                                4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        help center
ii  kinfocenter                                                 4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        system information viewer
ii  klipper                                                     4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        clipboard manager
ii  kmag                                                        4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        screen magnifier tool
ii  kmenuedit                                                   4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        XDG menu editor
ii  kmix                                                        4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        volume control and mixer
ii  kmousetool                                                  4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        mouse manipulation tool for the disabled
ii  kmouth                                                      4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        type-and-say frontend for speech synthesizers
ii  knotes                                                      4:4.10.0a-0ubuntu1~ubuntu12.04.2~ppa1            amd64        sticky notes application
ii  konsole                                                     4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        X terminal emulator
ii  konsole-dbg                                                 4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        debugging symbols for the KDE X terminal emulator
ii  krosspython                                                 4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        Python module for Kross
ii  kruler                                                      4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        screen ruler
ii  ksysguard                                                   4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        process monitor and system statistics
ii  ksysguardd                                                  4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        System Guard Daemon
ii  ksystemlog                                                  4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        system log viewer
ii  kwalletmanager                                              4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        secure password wallet manager
ii  libakonadi-calendar4                                        4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        library providing calendar helpers for Akonadi items
ii  libakonadi-contact4                                         4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        library for using the Akonadi PIM data server
ii  libakonadi-kabc4                                            4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        library for using the Akonadi PIM data server
ii  libakonadi-kcal4                                            4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        library for using the Akonadi PIM data server
ii  libakonadi-kde4                                             4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        library for using the Akonadi PIM data server
ii  libakonadi-kmime4                                           4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        library for using the Akonadi PIM data server
ii  libakonadi-notes4                                           4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        library providing notes helpers for Akonadi items
ii  libakonadi-socialutils4                                     4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        Akonadi resources for handling social feeds
ii  libaudiocdplugins4                                          4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        transparent audio CD access for applications using the KDE Platform
ii  libfreetype6:amd64                                          2.4.10-0ubuntu1.1                                amd64        FreeType 2 font engine, shared library files
ii  libfreetype6:i386                                           2.4.10-0ubuntu1.1                                i386         FreeType 2 font engine, shared library files
ii  libfreetype6-dev                                            2.4.10-0ubuntu1.1                                amd64        FreeType 2 font engine, development files
ii  libgpgme++2                                                 4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        c++ wrapper library for gpgme
ii  libkabc4                                                    4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        library for handling address book data
ii  libkactivities-bin                                          4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        executables for the KDE Activities
ii  libkactivities-dev                                          4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        development files for the KDE Activities libraries
ii  libkactivities-models1                                      4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        Activities models library
ii  libkactivities6                                             4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        Activities library
ii  libkalarmcal2                                               4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        library for handling kalarm calendar data
ii  libkateinterfaces4                                          4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        kate plugin interface library
ii  libkatepartinterfaces4                                      4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        kate part library
ii  libkblog4                                                   4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        client-side support library for web application remote blogging APIs
ii  libkcal4                                                    4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        library for handling calendar data
ii  libkcalcore4                                                4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        library for handling calendar data
ii  libkcalutils4                                               4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        library with utility functions for the handling of calendar data
ii  libkcddb4                                                   4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        CDDB library for KDE Platform (runtime)
ii  libkcmutils4                                                4:4.10.0-0ubuntu2~ubuntu12.04.2~ppa1             amd64        utility classes for using KCM modules
ii  libkcompactdisc4                                            4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        KDE library for interfacing with CDs
ii  libkde3support4                                             4:4.10.0-0ubuntu2~ubuntu12.04.2~ppa1             amd64        KDE 3 Support Library for the KDE 4 Platform
ii  libkdeclarative5                                            4:4.10.0-0ubuntu2~ubuntu12.04.2~ppa1             amd64        declarative library for plasma
ii  libkdecorations4abi1                                        4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        library used by decorations for the KDE window manager
ii  libkdecore5                                                 4:4.10.0-0ubuntu2~ubuntu12.04.2~ppa1             amd64        KDE Platform Core Library
ii  libkdepim4                                                  4:4.10.0a-0ubuntu1~ubuntu12.04.2~ppa1            amd64        KDE PIM library
ii  libkdesu5                                                   4:4.10.0-0ubuntu2~ubuntu12.04.2~ppa1             amd64        Console-mode Authentication Library for the KDE Platform
ii  libkdeui5                                                   4:4.10.0-0ubuntu2~ubuntu12.04.2~ppa1             amd64        KDE Platform User Interface Library
ii  libkdewebkit5                                               4:4.10.0-0ubuntu2~ubuntu12.04.2~ppa1             amd64        KDE WebKit Library
ii  libkdnssd4                                                  4:4.10.0-0ubuntu2~ubuntu12.04.2~ppa1             amd64        DNS-SD Protocol Library for the KDE Platform
ii  libkemoticons4                                              4:4.10.0-0ubuntu2~ubuntu12.04.2~ppa1             amd64        utility classes to deal with emoticon themes
ii  libkexiv2-data                                              4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             all          Qt-like interface for the libexiv2 library -- data files
ii  libkfile4                                                   4:4.10.0-0ubuntu2~ubuntu12.04.2~ppa1             amd64        File Selection Dialog Library for KDE Platform
ii  libkholidays4                                               4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        holidays calculation library
ii  libkhtml5                                                   4:4.10.0-0ubuntu2~ubuntu12.04.2~ppa1             amd64        KHTML Web Content Rendering Engine
ii  libkidletime4                                               4:4.10.0-0ubuntu2~ubuntu12.04.2~ppa1             amd64        library to provide information about idle time
ii  libkimap4                                                   4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        library for handling IMAP data
ii  libkimproxy4                                                4:4.10.0-0ubuntu2~ubuntu12.04.2~ppa1             amd64        Instant Messaging Interface Library for the KDE Platform
ii  libkio5                                                     4:4.10.0-0ubuntu2~ubuntu12.04.2~ppa1             amd64        Network-enabled File Management Library for the KDE Platform
ii  libkipi-data                                                4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             all          data files for kipi libraries
ii  libkjsapi4                                                  4:4.10.0-0ubuntu2~ubuntu12.04.2~ppa1             amd64        KJS API Library for the KDE Development Platform
ii  libkjsembed4                                                4:4.10.0-0ubuntu2~ubuntu12.04.2~ppa1             amd64        library for binding JavaScript objects to QObjects
ii  libkldap4                                                   4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        library for accessing LDAP
ii  libkmbox4                                                   4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        library for handling mbox mailboxes
ii  libkmediaplayer4                                            4:4.10.0-0ubuntu2~ubuntu12.04.2~ppa1             amd64        KMediaPlayer Interface for the KDE Platform
ii  libkmime4                                                   4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        library for handling MIME data
ii  libknewstuff2-4                                             4:4.10.0-0ubuntu2~ubuntu12.04.2~ppa1             amd64        "Get Hot New Stuff" v2 Library for the KDE Platform
ii  libknewstuff3-4                                             4:4.10.0-0ubuntu2~ubuntu12.04.2~ppa1             amd64        "Get Hot New Stuff" v3 Library for the KDE Platform
ii  libknotifyconfig4                                           4:4.10.0-0ubuntu2~ubuntu12.04.2~ppa1             amd64        library for configuring KDE Notifications
ii  libkntlm4                                                   4:4.10.0-0ubuntu2~ubuntu12.04.2~ppa1             amd64        NTLM Authentication Library for the KDE Platform
ii  libkonq-common                                              4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        core Konqueror library - support files
ii  libkonq5-dev                                                4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        development files for the Konqueror libraries
ii  libkonq5-templates                                          4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             all          data files for the Konqueror libraries
ii  libkonq5abi1                                                4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        core libraries for Konqueror
ii  libkonqsidebarplugin-dev                                    4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        konqueror sidebar plugin library development files
ii  libkonqsidebarplugin4a                                      4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        konqueror sidebar plugin library
ii  libkontactinterface4                                        4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        Kontact interface library
ii  libkparts4                                                  4:4.10.0-0ubuntu2~ubuntu12.04.2~ppa1             amd64        Framework for the KDE Platform Graphical Components
ii  libkpimidentities4                                          4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        library for managing user identities
ii  libkpimtextedit4                                            4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        library that provides a textedit with PIM-specific features
ii  libkpimutils4                                               4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        library for dealing with email addresses
ii  libkprintutils4                                             4:4.10.0-0ubuntu2~ubuntu12.04.2~ppa1             amd64        utility classes to deal with printing
ii  libkpty4                                                    4:4.10.0-0ubuntu2~ubuntu12.04.2~ppa1             amd64        Pseudo Terminal Library for the KDE Platform
ii  libkresources4                                              4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        KDE Resource framework library
ii  libkrosscore4                                               4:4.10.0-0ubuntu2~ubuntu12.04.2~ppa1             amd64        Kross Core Library
ii  libkrossui4                                                 4:4.10.0-0ubuntu2~ubuntu12.04.2~ppa1             amd64        Kross UI Library
ii  libksane-data                                               4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             all          scanner library (data files)
ii  libksane0                                                   4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        scanner library (runtime)
ii  libkscreensaver5                                            4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        library of the KDE Screensaver system
ii  libksgrd4                                                   4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        library for ksysguard
ii  libksignalplotter4                                          4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        KSignalPlotter widget
ii  libktexteditor4                                             4:4.10.0-0ubuntu2~ubuntu12.04.2~ppa1             amd64        KTextEditor interfaces for the KDE Platform
ii  libktnef4                                                   4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        library for handling TNEF data
ii  libkunitconversion4                                         4:4.10.0-0ubuntu2~ubuntu12.04.2~ppa1             amd64        Unit Conversion library for the KDE Platform
ii  libkutils4                                                  4:4.10.0-0ubuntu2~ubuntu12.04.2~ppa1             amd64        dummy transitional library
ii  libkwinactiveeffects1abi4                                   4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        library used by effects for the KDE window manager Active
ii  libkwinactiveglesutils1                                     4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        library used by accelleration for the KDE window manager Active
ii  libkwinactiveglutils1abi1                                   4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        library used by accellaration for the KDE window manager Active
ii  libkwinactivenvidiahack4                                    4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        library used by nvidia cards for the KDE window manager
ii  libkwineffects1abi4                                         4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        library used by effects for the KDE window manager
ii  libkwinglesutils1                                           4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        library used by accellaration for the KDE window manager
ii  libkwinglutils1abi1                                         4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        library used by accellaration for the KDE window manager
ii  libkwinnvidiahack4                                          4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        library used by nvidia cards for the KDE window manager
ii  libkxmlrpcclient4                                           4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        simple XML-RPC client library
ii  liblsofui4                                                  4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        library for ksysguard based priority scheduling
ii  libmailtransport4                                           4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        mail transport service library
ii  libmarblewidget15                                           4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        Marble globe widget library
ii  libmicroblog4                                               4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        library for using the Microblog Akonadi Resource
ii  libnepomuk4                                                 4:4.10.0-0ubuntu2~ubuntu12.04.2~ppa1             amd64        Nepomuk Meta Data Library
ii  libnepomukcore4abi1                                         4:4.10.0-0ubuntu2~ubuntu12.04.2~ppa1             amd64        The Nepomuk Meta Data Library
ii  libnepomukquery4a                                           4:4.10.0-0ubuntu2~ubuntu12.04.2~ppa1             amd64        Nepomuk Query Library for the KDE Platform
ii  libnepomukutils4                                            4:4.10.0-0ubuntu2~ubuntu12.04.2~ppa1             amd64        Nepomuk Utility Library
ii  libnepomukwidgets4                                          4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        The Nepomuk Semantik Desktop widgets library
ii  libokularcore2abi1                                          4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        libraries for the Okular document viewer
ii  libplasma-geolocation-interface4                            4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        library for the Plasma geolocation
ii  libplasma3                                                  4:4.10.0-0ubuntu2~ubuntu12.04.2~ppa1             amd64        Plasma Library for the KDE Platform
ii  libprocesscore4abi1                                         4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        library for ksysguard based process view
ii  libprocessui4a                                              4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        library for ksysguard process user interface
ii  libqgpgme1                                                  4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        library for GpgME++ integration with Qt
ii  libqtruby4shared2                                           4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        internal library for Qt 4 Ruby bindings
ii  librpm3                                                     4.10.0-4ubuntu0.1                                amd64        RPM shared library
ii  librpmbuild3                                                4.10.0-4ubuntu0.1                                amd64        RPM build shared library
ii  librpmio3                                                   4.10.0-4ubuntu0.1                                amd64        RPM IO shared library
ii  librpmsign1                                                 4.10.0-4ubuntu0.1                                amd64        RPM signing shared library
ii  libsmokebase3                                               4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        SMOKE base library
ii  libsmokekdecore4-3                                          4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        KDE Core SMOKE libraries
ii  libsmokekdeui4-3                                            4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        KDE Ui SMOKE libraries
ii  libsmokekfile3                                              4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        KFile SMOKE library
ii  libsmokekhtml3                                              4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        KHTML SMOKE library
ii  libsmokekio3                                                4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        KIO SMOKE library
ii  libsmokeknewstuff2-3                                        4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        KNewStuff2 SMOKE library
ii  libsmokeknewstuff3-3                                        4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        KNewStuff3 SMOKE library
ii  libsmokekparts3                                             4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        KParts SMOKE libraries
ii  libsmokektexteditor3                                        4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        KTextEditor SMOKE libraries
ii  libsmokekutils3                                             4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        KUtils SMOKE libraries
ii  libsmokenepomuk3                                            4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        Nepomuk SMOKE libraries
ii  libsmokeplasma3                                             4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        Plasma SMOKE library
ii  libsmokeqtcore4-3                                           4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        Qt Core SMOKE library
ii  libsmokeqtdbus4-3                                           4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        Qt D-Bus SMOKE library
ii  libsmokeqtgui4-3                                            4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        Qt Gui SMOKE library
ii  libsmokeqtnetwork4-3                                        4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        Qt Network SMOKE library
ii  libsmokeqtopengl4-3                                         4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        Qt OpenGL SMOKE library
ii  libsmokeqtsql4-3                                            4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        Qt Sql SMOKE library
ii  libsmokeqtsvg4-3                                            4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        Qt Svg SMOKE library
ii  libsmokeqtwebkit4-3                                         4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        Qt WebKit SMOKE library
ii  libsmokeqtxml4-3                                            4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        Qt Xml SMOKE library
ii  libsmokesolid3                                              4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        Solid SMOKE libraries
ii  libsolid4                                                   4:4.10.0-0ubuntu2~ubuntu12.04.2~ppa1             amd64        Solid Library for KDE Platform
ii  libsolidcontrol4abi2                                        4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        library for Solid based network management
ii  libsolidcontrolifaces4abi2                                  4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        library for Solid based network interface management
ii  libsyndication4                                             4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        parser library for RSS and Atom feeds
ii  libtaskmanager4abi3                                         4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        library which provides task management facilities
ii  libthreadweaver4                                            4:4.10.0-0ubuntu2~ubuntu12.04.2~ppa1             amd64        ThreadWeaver Library for the KDE Platform
ii  libweather-ion6                                             4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        library which provides an interface for weather information services
ii  marble-data                                                 4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             all          data files for Marble
ii  marble-plugins                                              4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        plugins for Marble
ii  nepomuk-core-data                                           4:4.10.0-0ubuntu2~ubuntu12.04.2~ppa1             all          Nepomuk Semantik Desktop core libraries -- shared data files
ii  nepomuk-core-dev                                            4:4.10.0-0ubuntu2~ubuntu12.04.2~ppa1             amd64        Nepomuk Semantik Desktop core libraries -- development files
ii  okular-extra-backends                                       4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        additional document format support for Okular
ii  oxygen-icon-theme                                           4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             all          Oxygen icon theme
ii  plasma-containments-addons                                  4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        additional containment plugins for Plasma
ii  plasma-dataengines-addons                                   4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        additional data engines for Plasma
ii  plasma-desktopthemes-artwork                                4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             all          desktop themes for KDE Plasma Workspaces
ii  plasma-runners-addons                                       4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        additional runners for Plasma and Krunner
ii  plasma-scriptengine-ruby                                    4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             all          Ruby script engine for Plasma
ii  plasma-scriptengine-webkit                                  4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        Web and Mac OS X dashboard widget support for Plasma
ii  plasma-widget-folderview                                    4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        plasma widget showing the content of a folder
ii  plasma-widget-kimpanel                                      4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        KIMPanel widget for Plasma
ii  print-manager                                               4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        printer config and monitor tool
ii  rpm                                                         4.10.0-4ubuntu0.1                                amd64        package manager for RPM
ii  rpm-common                                                  4.10.0-4ubuntu0.1                                amd64        common files for RPM
ii  rpm2cpio                                                    4.10.0-4ubuntu0.1                                amd64        tool to convert RPM package to CPIO archive
ii  ruby-kde4                                                   4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        KDE bindings for the Ruby language
ii  ruby-plasma                                                 4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        Plasma Ruby bindings
ii  ruby-qt4                                                    4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        Qt 4 bindings for the Ruby language
ii  ruby-qt4-webkit                                             4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        QtWebKit bindings for the Ruby language
ii  systemsettings                                              4:4.10.0-0ubuntu1~ubuntu12.04.2~ppa1             amd64        System Settings
ii  tasks-icons                                                 4:4.10.0a-0ubuntu1~ubuntu12.04.2~ppa1            all          icon files for the taks management
```Is there a way to batch-download or downgrade all of these?
I re-installed all these packages, and now it sort of seems to work, at least it appears normal.  Only time will tell now if anything's been really messed up.

---

### Post by Ravi5kumar on 2013-02-16
Thanks! I am not going to add the backports ppa now. ;)

---

### Post by speartip on 2013-02-16
I know some people have been having problems updating to 4.10, using the kubuntu backports ppa, but I think most of it is configuration conflicts, not a problem with the ppa itself.
I managed to successfully upgrade to 4.10 using:
```
sudo apt-get update && sudo apt-get upgrade && sudo apt-get dist upgrade 
```I encountered errors that were rectified by:
```
sudo apt-get -f install && sudo apt-get dist upgrade
```but something didn't seem right & I encountered a few plasma crashes.
So I deleted my .kde folder in /home & rebooted.
This meant I had to reconfigure all my personal settings, but it only took about 10 minutes.
Now 4.10 runs like a dream:D

---

### Post by orb9220 on 2013-02-16
Yep problem always seems to be a conflicting repo list.
Good point speartip about deleting .kde folder in /home tho and not file?
Unless you are talking about .kderc file?
.

---

### Post by speartip on 2013-02-17
> **orb9220 said:**
> Good point speartip about deleting .kde folder in /home tho and not file?
Good point orb9220, just edited my post accordingly.

---

