---
title: "Partial Upgrade - Not Working"
date: 2008-04-23
forum: Desktop Environments
---

### Post by drewdlephone on 2008-04-23
Hey everyone. I suppose I could wait one more day and get the full version of Hardy, but currently I'm running the Beta, and I wanted to move to the RC version, which I can do through Software Update. There's a catch, though. When I attempt the upgrade, I get this message:

```
The following packages could not be authenticated:

app-install-data
bluez-audio
bluez-cups
bluez-utils
cupsys
cupsys-bsd
cupsys-client
cupsys-common
desktop-file-utils
dictionaries-common
evolution
evolution-common
evolution-data-server
evolution-data-server-common
evolution-plugins
firefox
firefox-3.0
firefox-3.0-gnome-support
firefox-gnome-support
gdebi
gdebi-core
gdm
gnome-mount
gnome-system-tools
guidance-backends
gvfs
gvfs-backends
gvfs-fuse
hal
libcamel1.2-11
libcupsimage2
libcupsys2
libdecoration0
libebook1.2-9
libecal1.2-7
libedata-book1.2-2
libedata-cal1.2-6
libedataserver1.2-9
libedataserverui1.2-8
libegroupwise1.2-13
libexchange-storage1.2-3
libgdata-google1.2-1
libgdata1.2-1
libgvfscommon0
libhal-storage1
libhal1
linux-ubuntu-modules-2.6.24-16-generic
python2.5
python2.5-minimal
readahead
rhythmbox
seahorse
system-config-printer-common
system-config-printer-gnome
ubufox
ubuntu-desktop
ubuntu-minimal
ubuntu-standard
xkb-data
```

And it kicks me out. Is this just a bug in the RC, that will go away when the full version is released, or have I done something to the machine? Can I get around this?

---

### Post by rouge568 on 2008-04-23
Ok, so this is an authentication error, so first off disable any non-official repositories (anything other than main, restricted, universe, and multiverse) repositories, and then run 'sudo update-manager -p'. If it works, then you're golden. Update, re-enable your extra repositories, and upgrade everything else you have. 
If that doesn't work, upgrade only apt-install-data 'sudo apt-get upgrade apt-install-data' and try again (you may want to do this with gdebi and gdebi-core as well). If that doesn't work, wait a couple hours and try again. This might (but probably isn't) be an issue with the repositories.

And a point: the beta is a rolling release, and you already have the release candidate if you are staying upgraded. This goes for the final, too: you won't have to upgrade a million packages.

Let me know if this works for you!

---

### Post by atomkarinca on 2008-04-23
The simplest solution -that I know of- is this: open up the Synaptic Package Manager, hit "Mark All Upgrades" and hit "Apply". This should do the trick.

EDIT: The reason for this partial upgrade error should be this: most probably there are some packages that are needed to be removed, as the update manager can't remove packages it only allows to update the current packages. If you hit close and then manually select update it would finish with no problem, although without the packages that needs to be removed. But the above trick should work for all the upgrades.

---

### Post by Simoh1 on 2009-05-08
This also works in Intrepid 8.10 with a current issue. Openoffice won't upgrade to 3.1 from 3.0 automatically using Update Manager. Using Synaptic Package Manager to Mark all Upgrades then Apply ensures removal of old files and fixes the update errors.

---

