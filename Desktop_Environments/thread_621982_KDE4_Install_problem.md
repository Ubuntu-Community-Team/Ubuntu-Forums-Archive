---
title: "KDE4 Install problem"
date: 2007-11-24
forum: Desktop Environments
---

### Post by jasonlfunk on 2007-11-24
I was following the instructions on KDE's website about how to install KDE4 RC1. I added the repository and ran "sudo apt-get install kdebase-dev-kde4 kdebase-workspace-dev kdebase-runtime" and it errored while trying to install it. I'm not sure how to go about either making KDE4 successfully install, or have apt forget I was trying to install it. Either would be nice. Here is the error:
```

The following packages have unmet dependencies:
  kdebase-bin-kde4: Depends: kde-icons-oxygen but it is not going to be installed
                    Depends: kdebase-runtime-data but it is not going to be installed
                    Depends: libkonq5 but it is not going to be installed
  kdebase-data-kde4: Depends: kde-icons-oxygen (>= 4:3.96.0-1ubuntu1~ppa1) but it is not going to be installed
  kdebase-kde4: Depends: dolphin-kde4 (>= 4:3.96.0-1ubuntu1~ppa1) but it is not going to be installed
                Depends: kappfinder-kde4 (>= 4:3.96.0-1ubuntu1~ppa1) but it is not going to be installed
                Depends: kdepasswd-kde4 (>= 4:3.96.0-1ubuntu1~ppa1) but it is not going to be installed
                Depends: kfind-kde4 (>= 4:3.96.0-1ubuntu1~ppa1) but it is not going to be installed
                Depends: konqueror-nsplugins-kde4 (>= 4:3.96.0-1ubuntu1~ppa1) but it is not going to be installed
                Depends: konqueror-kde4 (>= 4:3.96.0-1ubuntu1~ppa1) but it is not going to be installed
                Depends: konsole-kde4 (>= 4:3.96.0-1ubuntu1~ppa1) but it is not going to be installed
                Depends: kwrite-kde4 (>= 4:3.96.0-1ubuntu1~ppa1) but it is not going to be installed
                Depends: libkonq5 (>= 4:3.96.0-1ubuntu1~ppa1) but it is not going to be installed
  kdebase-runtime: Depends: kdebase-runtime-data (>= 4:3.96.0-1ubuntu1~ppa1) but it is not going to be installed
                   Depends: kde-icons-oxygen (>= 4:3.96.0-1ubuntu1~ppa1) but it is not going to be installed
  kdebase-runtime-bin: Depends: kde-icons-oxygen but it is not going to be installed
                       Depends: kdebase-runtime-data but it is not going to be installed
                       Depends: kdebase-runtime-data (= 4:3.96.0-1ubuntu1~ppa1) but it is not going to be installed
  kdebase-runtime-bin-kde4: Depends: kde-icons-oxygen but it is not going to be installed
                            Depends: kdebase-runtime-data but it is not going to be installed
  kdebase-workspace-bin: Depends: kde-icons-oxygen but it is not going to be installed
                         Depends: kdebase-runtime-data but it is not going to be installed
  klipper-kde4: Depends: kde-icons-oxygen but it is not going to be installed
                Depends: kdebase-runtime-data but it is not going to be installed
  ksysguard-kde4: Depends: kde-icons-oxygen but it is not going to be installed
                  Depends: kdebase-runtime-data but it is not going to be installed
  kwin-kde4: Depends: kde-icons-oxygen but it is not going to be installed
             Depends: kdebase-runtime-data but it is not going to be installed
  libplasma1: Depends: kde-icons-oxygen but it is not going to be installed
              Depends: kdebase-runtime-data but it is not going to be installed
  systemsettings-kde4: Depends: kde-icons-oxygen but it is not going to be installed
                       Depends: kdebase-runtime-data but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```

Running 'apt=get -f install' yields:

```

funkja@niniel:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libxine-dev kde4base-data libslang2-dev
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  dolphin-kde4 kappfinder-kde4 kde-icons-oxygen kdebase-runtime-data kdepasswd-kde4 kfind-kde4 konqueror-kde4
  konqueror-nsplugins-kde4 konsole-kde4 kwrite-kde4 libkonq5
The following NEW packages will be installed:
  dolphin-kde4 kappfinder-kde4 kde-icons-oxygen kdebase-runtime-data kdepasswd-kde4 kfind-kde4 konqueror-kde4
  konqueror-nsplugins-kde4 konsole-kde4 kwrite-kde4 libkonq5
0 upgraded, 11 newly installed, 0 to remove and 14 not upgraded.
41 not fully installed or removed.
Need to get 0B/60.1MB of archives.
After unpacking 90.9MB of additional disk space will be used.
Do you want to continue [Y/n]? Y
WARNING: The following packages cannot be authenticated!
  kde-icons-oxygen kdebase-runtime-data libkonq5 dolphin-kde4 kappfinder-kde4 kdepasswd-kde4 kfind-kde4
  konqueror-nsplugins-kde4 konqueror-kde4 konsole-kde4 kwrite-kde4
Install these packages without verification [y/N]? y
(Reading database ... 117048 files and directories currently installed.)
Unpacking kde-icons-oxygen (from .../kde-icons-oxygen_4%3a3.96.0-1ubuntu1~ppa1_all.deb) ...
dpkg: error processing /var/cache/apt/archives/kde-icons-oxygen_4%3a3.96.0-1ubuntu1~ppa1_all.deb (--unpack):
 trying to overwrite `/usr/lib/kde4/share/icons/oxygen/scalable/emblems/emblem-mounted.svgz', which is also in package kde4base-data
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Unpacking kdebase-runtime-data (from .../kdebase-runtime-data_4%3a3.96.0-1ubuntu1~ppa1_all.deb) ...
dpkg: error processing /var/cache/apt/archives/kdebase-runtime-data_4%3a3.96.0-1ubuntu1~ppa1_all.deb (--unpack):
 trying to overwrite `/usr/lib/kde4/share/dbus-1/interfaces/org.kde.KTimeZoned.xml', which is also in package kde4base-data
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Unpacking libkonq5 (from .../libkonq5_4%3a3.96.0-1ubuntu1~ppa1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libkonq5_4%3a3.96.0-1ubuntu1~ppa1_i386.deb (--unpack):
 trying to overwrite `/usr/lib/kde4/share/dbus-1/interfaces/org.kde.libkonq.KonqHistoryManager.xml', which is also in package kde4base-data
Unpacking dolphin-kde4 (from .../dolphin-kde4_4%3a3.96.0-1ubuntu1~ppa1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/dolphin-kde4_4%3a3.96.0-1ubuntu1~ppa1_i386.deb (--unpack):
 trying to overwrite `/usr/lib/kde4/share/kde4/services/dolphinpart.desktop', which is also in package kde4base-data
Unpacking kappfinder-kde4 (from .../kappfinder-kde4_4%3a3.96.0-1ubuntu1~ppa1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/kappfinder-kde4_4%3a3.96.0-1ubuntu1~ppa1_i386.deb (--unpack):
 trying to overwrite `/usr/lib/kde4/share/icons/hicolor/32x32/apps/kappfinder.png', which is also in package kde4base-data
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Unpacking kdepasswd-kde4 (from .../kdepasswd-kde4_4%3a3.96.0-1ubuntu1~ppa1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/kdepasswd-kde4_4%3a3.96.0-1ubuntu1~ppa1_i386.deb (--unpack):
 trying to overwrite `/usr/lib/kde4/share/kde4/services/kcm_useraccount.desktop', which is also in package kde4base-data
Unpacking kfind-kde4 (from .../kfind-kde4_4%3a3.96.0-1ubuntu1~ppa1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/kfind-kde4_4%3a3.96.0-1ubuntu1~ppa1_i386.deb (--unpack):
 trying to overwrite `/usr/lib/kde4/share/icons/hicolor/32x32/apps/kfind.png', which is also in package kde4base-data
Unpacking konqueror-nsplugins-kde4 (from .../konqueror-nsplugins-kde4_4%3a3.96.0-1ubuntu1~ppa1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/konqueror-nsplugins-kde4_4%3a3.96.0-1ubuntu1~ppa1_i386.deb (--unpack):
 trying to overwrite `/usr/lib/kde4/share/dbus-1/interfaces/org.kde.nsplugins.class.xml', which is also in package kde4base-data
Unpacking konqueror-kde4 (from .../konqueror-kde4_4%3a3.96.0-1ubuntu1~ppa1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/konqueror-kde4_4%3a3.96.0-1ubuntu1~ppa1_i386.deb (--unpack):
 trying to overwrite `/usr/lib/kde4/share/dbus-1/interfaces/org.kde.Konqueror.Main.xml', which is also in package kde4base-data
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Unpacking konsole-kde4 (from .../konsole-kde4_4%3a3.96.0-1ubuntu1~ppa1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/konsole-kde4_4%3a3.96.0-1ubuntu1~ppa1_i386.deb (--unpack):
 trying to overwrite `/usr/lib/kde4/share/icons/hicolor/scalable/apps/konsole.svgz', which is also in package kde4base-data
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Unpacking kwrite-kde4 (from .../kwrite-kde4_4%3a3.96.0-1ubuntu1~ppa1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/kwrite-kde4_4%3a3.96.0-1ubuntu1~ppa1_i386.deb (--unpack):
 trying to overwrite `/usr/lib/kde4/share/applications/kde4/kwrite.desktop', which is also in package kde4base-data
Errors were encountered while processing:
 /var/cache/apt/archives/kde-icons-oxygen_4%3a3.96.0-1ubuntu1~ppa1_all.deb
 /var/cache/apt/archives/kdebase-runtime-data_4%3a3.96.0-1ubuntu1~ppa1_all.deb
 /var/cache/apt/archives/libkonq5_4%3a3.96.0-1ubuntu1~ppa1_i386.deb
 /var/cache/apt/archives/dolphin-kde4_4%3a3.96.0-1ubuntu1~ppa1_i386.deb
 /var/cache/apt/archives/kappfinder-kde4_4%3a3.96.0-1ubuntu1~ppa1_i386.deb
 /var/cache/apt/archives/kdepasswd-kde4_4%3a3.96.0-1ubuntu1~ppa1_i386.deb
 /var/cache/apt/archives/kfind-kde4_4%3a3.96.0-1ubuntu1~ppa1_i386.deb
 /var/cache/apt/archives/konqueror-nsplugins-kde4_4%3a3.96.0-1ubuntu1~ppa1_i386.deb
 /var/cache/apt/archives/konqueror-kde4_4%3a3.96.0-1ubuntu1~ppa1_i386.deb
 /var/cache/apt/archives/konsole-kde4_4%3a3.96.0-1ubuntu1~ppa1_i386.deb
 /var/cache/apt/archives/kwrite-kde4_4%3a3.96.0-1ubuntu1~ppa1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


```

---

### Post by jasonlfunk on 2007-11-24
With some help from the IRC guys. I had some excess KDE4 libs that had to be removed.

sudo apt-get --purge remove $(dpkg -l | egrep '(KDE 4|KDE PIM 4|-kde4)' |cut -d ' ' -f 3) kdebase-workspace kdebase-runtime kdebase-runtime-bin kdebase-workspace-bin kdebase-workspace-dev libplasma-dev libplasma1

---

### Post by JACooks on 2007-11-26
Tried to perform the fix, since I had the same issue, but only get this when running the above commands:
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package kdebase-runtime is not installed, so not removed
Package kdebase-runtime-bin is not installed, so not removed
Package kdebase-workspace-dev is not installed, so not removed
Package libplasma-dev is not installed, so not removed
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  libsoprano4: Depends: libclucene0ldbl (>= 0.9.20-1) but it is not going to be installed
  libstreamanalyzer0: Depends: libclucene0ldbl (>= 0.9.20-1) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```

My error on apt-get -f install is

```

Unpacking kde-icons-oxygen (from .../kde-icons-oxygen_4%3a3.96.0-1ubuntu1_all.deb) ...
dpkg: error processing /var/cache/apt/archives/kde-icons-oxygen_4%3a3.96.0-1ubuntu1_all.deb (--unpack):
 trying to overwrite `/usr/lib/kde4/share/icons/oxygen/128x128/apps/phonon-xine.png', which is also in package kde4base-data
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Unpacking kdebase-runtime-data (from .../kdebase-runtime-data_4%3a3.96.0-1ubuntu1_all.deb) ...
dpkg: error processing /var/cache/apt/archives/kdebase-runtime-data_4%3a3.96.0-1ubuntu1_all.deb (--unpack):
 trying to overwrite `/usr/lib/kde4/share/applications/kde4/knetattach.desktop', which is also in package kde4base-data
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/kde-icons-oxygen_4%3a3.96.0-1ubuntu1_all.deb
 /var/cache/apt/archives/kdebase-runtime-data_4%3a3.96.0-1ubuntu1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Any other suggestions?

---

### Post by Brando569 on 2007-11-27
everything installs correctly for me except when i try to install kdebase-workspace and kde4artwork-data synaptic gives me this error:

```
E: /var/cache/apt/archives/kwin-kde4_4%3a3.96.0-1ubuntu4~gutsy1_amd64.deb: trying to overwrite `/usr/lib/kde4/share/icons/crystalsvg/16x16/apps/kcmkwm.png', which is also in package kde4artwork-data
```

---

