---
title: "Broken packages galore!"
date: 2005-12-15
forum: General Help
---

### Post by abyss6 on 2005-12-15
While trying to update my system so that automatix would work correctly, I think I may have screwed things up.  I have six broken packages: "cpp-4.0", "g++-4.0", "gcc-4.0", "gij-4.0", "libgcj6" and "libstdc++6-4.0-dev".  When I try to reinstall/remove these packages, it says that some packages have to be removed and it gives me a list of about 100 packages, a lot of them major.  What can I do to fix this?!?  Thanks.

---

### Post by super on 2005-12-15
try running:
[FONT="Courier New"]sudo apt-get install -f[/FONT]
that should allow apt-get to correct any broken packages.

alternately you can start synaptic and select 'fix broken' and then hit the 'apply' button.

---

### Post by abyss6 on 2005-12-16
This is what I get when I do the *install -f* command at the prompt:

```
The following packages will be REMOVED:
  bluez-pin bsh bug-buddy build-essential capplets-data contact-lookup-applet
  cpp cpp-4.0 debhelper dh-buildinfo eog evince evolution
  evolution-data-server evolution-exchange evolution-plugins evolution-webcal
  file-roller firefox firefox-gnome-support firestarter g++ g++-4.0 galeon
  gcalctool gcc gcc-4.0 gconf-editor gconf2 gdesklets gdesklets-data gdm gedit
  gettext gij gij-4.0 gnome-about gnome-app-install gnome-applets
  gnome-applets-data gnome-btdownload gnome-control-center gnome-cups-manager
  gnome-games gnome-media gnome-netstatus-applet gnome-nettool gnome-panel
  gnome-panel-data gnome-pilot gnome-pilot-conduits gnome-session gnome-spell
  gnome-system-monitor gnome-system-tools gnome-terminal gnome-utils
  gnome-volume-manager gnomebaker gnomemeeting gstreamer0.8-gnomevfs
  gstreamer0.8-misc gstreamer0.8-plugins gstreamer0.8-vorbis gthumb gtkhtml3.8
  gucharmap hal-device-manager hwdb-client intltool-debian java-gcj-compat
  libbonobo2-0 libbonobo2-common libbonoboui2-0 libcamel1.2-6 libebook1.2-5
  libecal1.2-3 libedata-book1.2-2 libedata-cal1.2-1 libedataserver1.2-4
  libedataserverui1.2-6 libeel2-2 libegroupwise1.2-8 libexchange-storage1.2-0
  libgcj6 libgcj6-common libgconf2-4 libgnome-desktop-2 libgnome2-0
  libgnome2-common libgnome2-perl libgnome2-vfs-perl libgnomecupsui1.0-1
  libgnomeui-0 libgnomevfs2-0 libgnomevfs2-common libgnucrypto-java
  libgnujaxp-java libgsf-1 libgstreamer-gconf0.8-0 libgtkhtml3.8-15
  libgucharmap4 libhsqldb-java libidl0 libjaxp1.2-java libjessie-java
  liblpint-bonobo0 libmetacity0 libnautilus-extension1 liborbit2
  libpanel-applet2-0 librsvg2-2 librsvg2-common libservlet2.3-java
  libstdc++6-4.0-dev libtotem-plparser0 libxalan2-java libxerces2-java
  libxt-java metacity nautilus nautilus-cd-burner nautilus-sendto
  openoffice.org2 openoffice.org2-base openoffice.org2-calc
  openoffice.org2-common openoffice.org2-core openoffice.org2-draw
  openoffice.org2-evolution openoffice.org2-gnome openoffice.org2-impress
  openoffice.org2-java-common openoffice.org2-l10n-en-us openoffice.org2-math
  openoffice.org2-writer po-debconf python-gnome2 python-gnome2-extras
  python-pyorbit python-uno python2.4-gnome2 python2.4-gnome2-extras
  python2.4-pyorbit rhythmbox serpentine sound-juicer totem totem-gstreamer
  tsclient ubuntu-desktop update-manager update-notifier vino yelp
```

---

### Post by super on 2005-12-16
whoa! don't do it then! :eek: 

try [FONT="Courier New"]sudo apt-get dist-upgrade[/FONT]
or if that won't work try [FONT="Courier New"]sudo apt-get install ubuntu-desktop[/FONT]

---

### Post by abyss6 on 2005-12-17
No luck.  This is what I get:

```
The following packages have unmet dependencies:
  cpp-4.0: Depends: gcc-4.0-base (= 4.0.1-4ubuntu9) but 4.0.2-5 is to be installed
  g++-4.0: Depends: gcc-4.0 (= 4.0.2-5) but 4.0.1-4ubuntu9 is to be installed
  gcc-4.0: Depends: gcc-4.0-base (= 4.0.1-4ubuntu9) but 4.0.2-5 is to be installed
  gij-4.0: Depends: gcc-4.0-base (= 4.0.1-4ubuntu9) but 4.0.2-5 is to be installed
  libgcj6: Depends: gcc-4.0-base (= 4.0.1-4ubuntu9) but 4.0.2-5 is to be installed
  libstdc++6-4.0-dev: Depends: libc6-dev (>= 2.3.5-5) but 2.3.5-1ubuntu12 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```

Those are the main broken packages.

Am I going to have to start over and reinstall?

---

### Post by super on 2005-12-17
looks like a problem with the package version numbers. do you have any unofficial repos in your sources.list?
if yes then comment them out and try again.
if not then i don't have any more answers for you.

sorry. :(

---

### Post by abyss6 on 2005-12-17
Thanks for the help - I reinstalled Breezy and things are working much better now.

---

