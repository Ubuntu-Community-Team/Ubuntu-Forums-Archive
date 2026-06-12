---
title: "gnome updates?"
date: 2010-11-30
forum: Desktop Environments
---

### Post by KegHead on 2010-11-30
Hi!

I ran the following in terminal:

sudo aptitude install gnome

I got about 20 files to be downloaded.

Any reason to download?

Thanks!

KegHead

---

### Post by Dans564 on 2010-11-30
> **KegHead said:**
> Hi!

I ran the following in terminal:

sudo aptitude install gnome

I got about 20 files to be downloaded.

Any reason to download?

Thanks!

KegHead

Don't you already have Gnome?? or areu on Kubuntu?

---

### Post by KegHead on 2010-11-30
Hi!

I have gnome 2.32 on Ubuntu 10.10

jim@jim-desktop:~$ sudo aptitude install gnome
The following NEW packages will be installed:
  abiword{a} abiword-common{a} abiword-plugin-grammar{a} 
  abiword-plugin-mathview{a} alsa-oss{a} arj{a} browser-plugin-gnash{a} 
  cheese{a} cheese-common{a} dasher{a} dasher-data{a} deskbar-applet{a} 
  desktop-base{a} ekiga{a} epiphany-extensions{a} festival{a} 
  festlex-cmu{a} festlex-poslex{a} festvox-kallpc16k{a} gedit-plugins{a} 
  gnash{a} gnash-common{a} gnome gnome-accessibility{a} 
  gnome-backgrounds{a} gnome-core{a} gnome-desktop-environment{a} 
  gnome-games-extra-data{a} gnome-netstatus-applet{a} gnome-office{a} 
  gnome-themes{a} gnome-themes-extras{a} gnome-themes-more{a} 
  gnome-user-share{a} gnumeric{a} gnumeric-common{a} gnumeric-doc{a} gok{a} 
  gparted{a} grdc{a} gthumb{a} gthumb-data{a} gtk2-engines-smooth{a} 
  hamster-applet{a} hardinfo{a} inkscape{a} libabiword-2.8{a} 
  libaiksaurus-1.2-0c2a{a} libaiksaurus-1.2-data{a} 
  libaiksaurusgtk-1.2-0c2a{a} libblas3gf{a} libboost-date-time1.42.0{a} 
  libboost-thread1.42.0{a} libcheese-gtk18{a} libdiscid0{a} 
  libestools2.0{a} libfreerdp-plugins-standard{a} libfreerdp0{a} 
  libgdome2-0{a} libgdome2-cpp-smart0c2a{a} libgfortran3{a} 
  libgnome-speech7{a} libgoffice-0.8-8{a} libgoffice-0.8-8-common{a} 
  libgtkmathview0c2a{a} libjpeg8{a} liblapack3gf{a} liblink-grammar4{a} 
  libmagick++3{a} libmusicbrainz3-6{a} libopal3.6.8{a} libots0{a} 
  libpsiconv6{a} libpt2.6.7{a} libsrtp0{a} libssh-4{a} libwmf-bin{a} 
  libwv-1.2-3{a} liferea{a} liferea-data{a} link-grammar-dictionaries-en{a} 
  menu-xdg{a} oss-compat{a} perlmagick{a} planner{a} python-evolution{a} 
  python-gnomedesktop{a} python-numpy{a} python-renderpm{a} 
  python-reportlab{a} python-reportlab-accel{a} python-uniconvertor{a} 
  remmina{a} remmina-plugin-data{a} remmina-plugin-rdp{a} 
  remmina-plugin-vnc{a} seahorse-plugins{a} sound-juicer{a} swfdec-gnome{a} 
  swfdec-mozilla{a} w3c-dtd-xhtml{a} 
0 packages upgraded, 101 newly installed, 0 to remove and 0 not upgraded.
Need to get 131MB of archives. After unpacking 379MB will be used.
The following packages have unmet dependencies:
  epiphany-browser: Conflicts: swfdec-mozilla but 0.8.8-5ubuntu1 is to be installed.
The following actions will resolve these dependencies:

     Keep the following packages at their current version:
1)     gnome [Not Installed]                              
2)     swfdec-mozilla [Not Installed]                     



Accept this solution? [Y/n/q/?]

---

### Post by wojox on 2010-11-30
That's not how you update. ;)

```
sudo aptitude update
```

```
sudo aptitude safe-upgrade
```

---

### Post by KegHead on 2010-11-30
Hi!

I ran:

sudo apt-get update before the command.

I'm just curious about the ugrades to gnome.

Any thoughts?

Thanks!

KegHead

---

### Post by wojox on 2010-11-30
What does 

```
sudo aptitude gnome-core
```

Tell you.

---

### Post by KegHead on 2010-11-30
jim@jim-desktop:~$ sudo aptitude gnome-core
Unknown command "gnome-core"
aptitude 0.6.3
Usage: aptitude [-S fname] [-u|-i]
       aptitude [options] <action> ...
  Actions (if none is specified, aptitude will enter interactive mode):

 install      - Install/upgrade packages.
 remove       - Remove packages.
 purge        - Remove packages and their configuration files.
 hold         - Place packages on hold.
 unhold       - Cancel a hold command for a package.
 markauto     - Mark packages as having been automatically installed.
 unmarkauto   - Mark packages as having been manually installed.
 forbid-version - Forbid aptitude from upgrading to a specific package version.
 update       - Download lists of new/upgradable packages.
 safe-upgrade - Perform a safe upgrade.
 full-upgrade - Perform an upgrade, possibly installing and removing packages.
 build-dep    - Install the build-dependencies of packages.
 forget-new   - Forget what packages are "new".
 search       - Search for a package by name and/or expression.
 show         - Display detailed information about a package.
 clean        - Erase downloaded package files.
 autoclean    - Erase old downloaded package files.
 changelog    - View a package's changelog.
 download     - Download the .deb file for a package.
 reinstall    - Download and (possibly) reinstall a currently installed package.
 why          - Show the manually installed packages that require a package, or
                why one or more packages would require the given package
 why-not      - Show the manually installed packages that lead to a conflict
                with the given package, or why one or more packages would
                lead to a conflict with the given package if installed.

  Options:
 -h             This help text.
 --no-gui       Do not use the GTK GUI even if available.
 -s             Simulate actions, but do not actually perform them.
 -d             Only download packages, do not install or remove anything.
 -P             Always prompt for confirmation or actions.
 -y             Assume that the answer to simple yes/no questions is 'yes'.
 -F format      Specify a format for displaying search results; see the manual.
 -O order       Specify how search results should be sorted; see the manual.
 -w width       Specify the display width for formatting search results.
 -f             Aggressively try to fix broken packages.
 -V             Show which versions of packages are to be installed.
 -D             Show the dependencies of automatically changed packages.
 -Z             Show the change in installed size of each package.
 -v             Display extra information. (may be supplied multiple times).
 -t [release]   Set the release from which packages should be installed.
 -q             In command-line mode, suppress the incremental progress.
                indicators.
 -o key=val     Directly set the configuration option named 'key'.
 --with(out)-recommends	Specify whether or not to treat recommends as.
                strong dependencies.
 -S fname       Read the aptitude extended status info from fname.
 -u             Download new package lists on startup.
                  (terminal interface only) -i             Perform an install run on startup.
                  (terminal interface only)
                  This aptitude does not have Super Cow Powers.
jim@jim-desktop:~$ sudo aptitude gnome-core
Unknown command "gnome-core"
aptitude 0.6.3
Usage: aptitude [-S fname] [-u|-i]
       aptitude [options] <action> ...
  Actions (if none is specified, aptitude will enter interactive mode):

 install      - Install/upgrade packages.
 remove       - Remove packages.
 purge        - Remove packages and their configuration files.
 hold         - Place packages on hold.
 unhold       - Cancel a hold command for a package.
 markauto     - Mark packages as having been automatically installed.
 unmarkauto   - Mark packages as having been manually installed.
 forbid-version - Forbid aptitude from upgrading to a specific package version.
 update       - Download lists of new/upgradable packages.
 safe-upgrade - Perform a safe upgrade.
 full-upgrade - Perform an upgrade, possibly installing and removing packages.
 build-dep    - Install the build-dependencies of packages.
 forget-new   - Forget what packages are "new".
 search       - Search for a package by name and/or expression.
 show         - Display detailed information about a package.
 clean        - Erase downloaded package files.
 autoclean    - Erase old downloaded package files.
 changelog    - View a package's changelog.
 download     - Download the .deb file for a package.
 reinstall    - Download and (possibly) reinstall a currently installed package.
 why          - Show the manually installed packages that require a package, or
                why one or more packages would require the given package
 why-not      - Show the manually installed packages that lead to a conflict
                with the given package, or why one or more packages would
                lead to a conflict with the given package if installed.

  Options:
 -h             This help text.
 --no-gui       Do not use the GTK GUI even if available.
 -s             Simulate actions, but do not actually perform them.
 -d             Only download packages, do not install or remove anything.
 -P             Always prompt for confirmation or actions.
 -y             Assume that the answer to simple yes/no questions is 'yes'.
 -F format      Specify a format for displaying search results; see the manual.
 -O order       Specify how search results should be sorted; see the manual.
 -w width       Specify the display width for formatting search results.
 -f             Aggressively try to fix broken packages.
 -V             Show which versions of packages are to be installed.
 -D             Show the dependencies of automatically changed packages.
 -Z             Show the change in installed size of each package.
 -v             Display extra information. (may be supplied multiple times).
 -t [release]   Set the release from which packages should be installed.
 -q             In command-line mode, suppress the incremental progress.
                indicators.
 -o key=val     Directly set the configuration option named 'key'.
 --with(out)-recommends	Specify whether or not to treat recommends as.
                strong dependencies.
 -S fname       Read the aptitude extended status info from fname.
 -u             Download new package lists on startup.
                  (terminal interface only) -i             Perform an install run on startup.
                  (terminal interface only)
                  This aptitude does not have Super Cow Powers.
jim@jim-desktop:~$

---

### Post by wojox on 2010-11-30
Sorry, forgot the install. :oops:

```
sudo aptitude install gnome-core
```

---

### Post by KegHead on 2010-11-30
jim@jim-desktop:~$ sudo aptitude install gnome-core
The following NEW packages will be installed:
  gnome-core 
0 packages upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 16.8kB of archives. After unpacking 45.1kB will be used.
Get:1 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/universe gnome-core i386 1:2.28+1ubuntu4 [16.8kB]
Fetched 16.8kB in 0s (23.8kB/s)   
Selecting previously deselected package gnome-core.
(Reading database ... 144698 files and directories currently installed.)
Unpacking gnome-core (from .../gnome-core_1%3a2.28+1ubuntu4_i386.deb) ...
Setting up gnome-core (1:2.28+1ubuntu4) ...
                                         
jim@jim-desktop:~$

---

### Post by wojox on 2010-11-30
Personally I would keep my whole system updated. Not just Gnome. You will run into dependency hell. ;)

---

### Post by KegHead on 2010-11-30
thanks!

that's my game plan!

KegHead

---

