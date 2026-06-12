---
title: "Attempting to Install KDE on Ubuntu 6.06 [Resolved]"
date: 2007-01-07
forum: Desktop Environments
---

### Post by sluzi26 on 2007-01-07
Trying to instal KDE over Ubuntu 6.06 Dapper LTS using sudo apt-get install kubuntu-desktop

I receive the following errors:

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
                   Depends: akregator but it is not installable
                   Depends: amarok but it is not installable
                   Depends: ark but it is not installable
                   Depends: arts but it is not installable
                   Depends: bogofilter but it is not installable
                   Depends: gtk2-engines-gtk-qt but it is not installable
                   Depends: gwenview but it is not installable
                   Depends: k3b but it is not installable
                   Depends: kaddressbook but it is not installable
                   Depends: kaffeine-xine but it is not installable
                   Depends: kamera but it is not installable
                   Depends: karm but it is not installable
                   Depends: katapult but it is not installable
                   Depends: kate but it is not going to be installed
                   Depends: kaudiocreator but it is not installable
                   Depends: kcontrol but it is not going to be installed
                   Depends: kcron but it is not installable
                   Depends: kde-guidance but it is not going to be installed
                   Depends: kde-systemsettings but it is not installable
                   Depends: kdeadmin-kfile-plugins but it is not installable
                   Depends: kdebase-kio-plugins but it is not going to be installed
                   Depends: kdebluetooth but it is not installable
                   Depends: kdegraphics-kfile-plugins but it is not installable
                   Depends: kdemultimedia-kfile-plugins but it is not installable
                   Depends: kdemultimedia-kio-plugins but it is not installable
                   Depends: kdenetwork-filesharing but it is not going to be installed
                   Depends: kdenetwork-kfile-plugins but it is not going to be installed
                   Depends: kdepasswd but it is not going to be installed
                   Depends: kdepim-kio-plugins but it is not installable
                   Depends: kdepim-wizards but it is not installable
                   Depends: kdeprint but it is not going to be installed
                   Depends: kdesktop but it is not going to be installed
                   Depends: kdm but it is not going to be installed
                   Depends: kdnssd but it is not going to be installed
                   Depends: keep but it is not installable
                   Depends: kfind but it is not going to be installed
                   Depends: kghostview but it is not installable
                   Depends: khelpcenter but it is not going to be installed
                   Depends: kicker but it is not going to be installed
                   Depends: kio-apt but it is not installable
                   Depends: kio-locate but it is not installable
                   Depends: klaptopdaemon but it is not installable
                   Depends: klipper but it is not going to be installed
                   Depends: kmail but it is not installable
                   Depends: kmailcvt but it is not installable
                   Depends: kmenuedit but it is not going to be installed
                   Depends: kmilo but it is not installable
                   Depends: kmix but it is not installable
                   Depends: kmplayer-konq-plugins but it is not installable
                   Depends: knetworkconf but it is not installable
                   Depends: knotes but it is not installable
                   Depends: konq-plugins but it is not installable
                   Depends: konqueror but it is not going to be installed
                   Depends: konqueror-nsplugins but it is not going to be installed
                   Depends: konsole but it is not going to be installed
                   Depends: kontact but it is not installable
                   Depends: konversation but it is not installable
                   Depends: kooka but it is not installable
                   Depends: kopete but it is not going to be installed
                   Depends: korganizer but it is not installable
                   Depends: kpdf but it is not installable
                   Depends: kpf but it is not going to be installed
                   Depends: kppp but it is not going to be installed
                   Depends: krdc but it is not going to be installed
                   Depends: krfb but it is not going to be installed
                   Depends: krita but it is not installable
                   Depends: kscd but it is not installable
                   Depends: kscreensaver but it is not installable
                   Depends: ksmserver but it is not going to be installed
                   Depends: ksnapshot but it is not installable
                   Depends: ksplash but it is not going to be installed
                   Depends: ksplash-engine-moodin but it is not installable
                   Depends: ksvg but it is not installable
                   Depends: ksysguard but it is not going to be installed
                   Depends: ksystemlog but it is not installable
                   Depends: ktorrent but it is not installable
                   Depends: kubuntu-default-settings but it is not going to be installed
                   Depends: kubuntu-docs but it is not going to be installed
                   Depends: kubuntu-konqueror-shortcuts but it is not installable
                   Depends: kwalletmanager but it is not installable
                   Depends: kwin but it is not going to be installed
                   Depends: language-selector-qt but it is not going to be installed
                   Depends: libarts1-akode but it is not installable
                   Depends: libnss-mdns but it is not installable
                   Depends: openoffice.org-kde but it is not going to be installed
                   Depends: qca-tls but it is not installable
                   Depends: scim-qtimm but it is not installable
                   Depends: skim but it is not installable
                   Depends: speedcrunch but it is not installable
                   Depends: vorbis-tools but it is not installable
                   Depends: wlassistant but it is not installable

Thanks :)

D'oh, forgot to fix my repositories. Fixed it. Thanks anyway!

---

### Post by meng on 2007-01-07
Hmm, not sure of the answer, but try posting the contents of your /etc/apt/sources.list:

cat /etc/apt/sources.list

I wonder if this could be because you still have the CD-ROM listed as a source (I doubt it though). No harm in editing the sources.list to remove the CD-ROM as a repository (comment out by putting # at the front of the line).

---

