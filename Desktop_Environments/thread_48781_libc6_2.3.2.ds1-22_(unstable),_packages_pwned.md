---
title: "libc6 2.3.2.ds1-22 (unstable), packages pwned"
date: 2005-07-13
forum: Desktop Environments
---

### Post by royg1234 on 2005-07-13
I installed **libc6_2.3.2.ds1-22_i386.deb**, then **gtk2-engines-clearlooks_0.6.2-1_i386.deb**.  It did okay.  Then I decided to install  mergeant via synaptic, and as part of the install, it decided to remove the stuff below.

If I try to uninstall libc6, a LONG list of stuff to remove gets proposed.  And I can't just re-install the Ubuntu-approved libc6-i686, because it "**PreDepends: libc6 (=2.3.2.ds1-20ubuntu13) but 2.3.2.ds1-22 is to be installed**". How do I fix this?

> 
build-essential
tomboy
libdbus-cil
dbus-glib-1-dev
digikamimageplugins
digikam
g++
libgaldemm-2.4-dev
libgtkmm-2.4-dev
libglibmm-2.4-dev
libsigc++-2.0-dev
glade-gnome-2
gnome-common
kubuntu-desktop
libglade2-dev
libbz2-dev
libgstreamer0.8-dev
libxml2-dev
libpango1.0-dev
libxft-dev
libimlib2-dev
libpng12-dev
libmysqlclient12-dev
libfontconfig1-dev
libfreetype6-dev
zliblg-dev
libtiff4-dev
libxrender-dev
libungif4-dev
libtool
libpopt-dev
libjpeg62-dev
libmono-dev
libglib2.0-dev
liboggflac++-dev
liboggflac-dev
libflac++-dev
libflac-dev
libexpat1-dev
ubuntu-desktop
lsb
ubuntu-base
libc6-i686
libstdc++5-3.3-dev
g++-3.4
libstdc++6-dev
language-pack-en-base
locales
libstdc++2.10-dev
g++-dev
language-pack-en
libxi-dev
libx11-dev
libxext-dev
g++-2.95


---

### Post by royg1234 on 2005-07-14
I think I'm just gonna completely reinstall Ubuntu, but I've never done it before.  Can it be done without formatting?

---

### Post by NeoChaosX on 2005-07-14
libc is an critical part of Ubuntu. By installing a newer version, almost all the apps you listed need to be recompiled with it to work.

So yeah, a formatting is unavoidable.

---

### Post by royg1234 on 2005-07-14
is there any way to "undo" this?  I haven't restarted my computer, and I notice that the apps that it uninstalled are still there (at least Tomboy) and working, so I assume they're there, to be removed on restart.

Or if this is crazy talk, and I can't avoid formatting, is there a good strategy to making my system as close as possible to the previous one?

---

### Post by NeoChaosX on 2005-07-14
Did you try a Force Version in Synaptic (Package -> Force Version)? That could save your system.

---

### Post by royg1234 on 2005-07-14
Thanks!  Not fully resolved yet, though.

so I "force version"ed libc6-2.3.2ds1-22 back to the hoary version.  the "to be removed" list is now less crazy (the list resulting from a "mark for removal" was so long that the list took 20 seconds to build):

> 
epiphany-browser
epiphany-extensions
gdm
gtk2-engines-clearlooks
ubuntu-artwork


Proceed?  Anything else I need to do?  (I'm pretty worried about that "gdm" item--isn't that the login screen?).  And will I be able to reinstall the stuff that I lost (in first post)?

---

### Post by NeoChaosX on 2005-07-14
Was everything you listed in the first post uninstalled? Or is just those six that are slated to be removed?

---

### Post by royg1234 on 2005-07-14
everything in the first post is already uninstalled.  The new list is of the ones *to be uninstalled* if I go through with "force version"ing libc6 back into the hoary version.

---

### Post by NeoChaosX on 2005-07-15
Um, damn.

Backup your critical/personal files, do the force version, try to at least reinstall GDM. If that works, reinstall everything else.

---

### Post by royg1234 on 2005-07-20
Can I just back up my whole home folder (hidden files and all), and paste it into the fresh install?  Will this work, and are ALL of my settings stored here?

---

### Post by royg1234 on 2005-07-29
what are some text files are should save?  I remember messing with a bunch a while back, but I forgot what they are and where.  (like grub, and that file that changes the screen resolution).

---

