---
title: "Lubuntu 19.04 has KDE, Gnome, GTK and Qt - which of them  can be removed?"
date: 2019-06-07
forum: Desktop Environments
---

### Post by &amp;wP*!) on 2019-06-07
Hi all,

I have 19.04 Disco:
```
$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 19.04
Release:        19.04
Codename:       disco

```

But I have GNOME, KDE, LXQt and GTK. I'm bit confused. 

**Gnome**
```
$ sudo apt list --installed '*gnome*'
Listing... Done
gnome-accessibility-themes/disco,now 3.28-1ubuntu1 all [installed,automatic]
gnome-icon-theme/disco,now 3.12.0-3 all [installed,automatic]
gnome-keyring-pkcs11/disco,now 3.31.91-1ubuntu1 amd64 [installed,automatic]
**gnome-keyring/disco,now 3.31.91-1ubuntu1 amd64 [installed,automatic]**
gnome-themes-extra-data/disco,now 3.28-1ubuntu1 all [installed,automatic]
gnome-themes-extra/disco,now 3.28-1ubuntu1 amd64 [installed,automatic]
libpam-gnome-keyring/disco,now 3.31.91-1ubuntu1 amd64 [installed,automatic]
libsoup-gnome2.4-1/disco,now 2.66.1-1 amd64 [installed,automatic]
pinentry-gnome3/disco,now 1.1.0-1build2 amd64 [installed,automatic]

```
For example, following packages are dependent on **gnome-keyring**:
```
$ sudo apt rdepends gnome-keyring | grep Depends

WARNING: apt does not have a stable CLI interface. Use with caution in scripts.

Reverse Depends:
  Depends: gnome-core (>= 3.28)
**  Depends: ubuntu-budgie-desktop**
  Depends: python-ubuntu-kylin-sso-client
  Depends: pan
 |Depends: geary
  Depends: seahorse (>= 3.4)
  Depends: evolution-data-server
```

**Question on Gnome: **I have already lubuntu-desktop. Why should be there a ubuntu-budgie-desktop? Why do I have Gnome in Lubuntu? Can I remove all Gnome packages safely on Lubuntu?

**KDE:**
```

$ sudo apt list --installed '*kde*'
Listing... Done
debconf-kde-data/disco,now 1.0.3-1 all [installed,automatic]
debconf-kde-helper/disco,now 1.0.3-1 amd64 [installed,automatic]
kde-cli-tools-data/disco,now 4:5.15.4-0ubuntu1 all [installed,automatic]
kde-cli-tools/disco,now 4:5.15.4-0ubuntu1 amd64 [installed,automatic]
kde-style-breeze/disco,now 4:5.15.4.1-0ubuntu1 amd64 [installed]
libblockdev-crypto2/disco,now 2.20-7 amd64 [installed,automatic]
libblockdev-fs2/disco,now 2.20-7 amd64 [installed,automatic]
libblockdev-loop2/disco,now 2.20-7 amd64 [installed,automatic]
libblockdev-part-err2/disco,now 2.20-7 amd64 [installed,automatic]
libblockdev-part2/disco,now 2.20-7 amd64 [installed,automatic]
libblockdev-swap2/disco,now 2.20-7 amd64 [installed,automatic]
libblockdev-utils2/disco,now 2.20-7 amd64 [installed,automatic]
libblockdev2/disco,now 2.20-7 amd64 [installed,automatic]
libdebconf-kde1/disco,now 1.0.3-1 amd64 [installed,automatic]
polkit-kde-agent-1/disco,now 4:5.15.4-0ubuntu1 amd64 [installed,automatic]
qml-module-org-kde-bluezqt/disco,now 5.56.0-0ubuntu1 amd64 [installed,automatic]
qml-module-org-kde-kconfig/disco,now 5.56.0-0ubuntu1 amd64 [installed,automatic]
qml-module-org-kde-kcoreaddons/disco,now 5.56.0-0ubuntu1 amd64 [installed,automatic]
qml-module-org-kde-kio/disco,now 5.56.0-0ubuntu1 amd64 [installed,automatic]
qml-module-org-kde-kirigami2/disco,now 5.56.1-0ubuntu1 amd64 [installed,automatic]
qml-module-org-kde-kquickcontrols/disco,now 5.56.0-0ubuntu1 amd64 [installed,automatic]
qml-module-org-kde-kquickcontrolsaddons/disco,now 5.56.0-0ubuntu1 amd64 [installed,automatic]
qml-module-org-kde-newstuff/disco,now 5.56.0-0ubuntu1 amd64 [installed,automatic]
qml-module-org-kde-qqc2desktopstyle/disco,now 5.56.0-0ubuntu2 amd64 [installed,automatic]
usb-creator-kde/disco,now 0.3.5 amd64 [installed]
**xdg-desktop-portal-kde/disco,now 5.15.4-0ubuntu1 amd64 [installed,automatic]**

```

I have  XDG_CURRENT_DESKTOP=LXQt. **Question on KDE: **Why do I have e.g. **xdg-desktop-portal-kde**? Since I have LXQt, can I safely remove this?

**Question on KDE: **Is KDE built on Qt in Lubuntu?

The reason of the question is, that I see following dependencies for Kcalc:
```
$ sudo apt depends kcalc
kcalc
  Depends: libc6 (>= 2.29)
  Depends: libgcc1 (>= 1:3.0)
  Depends: libgmp10
  Depends: libkf5configcore5 (>= 4.98.0)
  Depends: libkf5configgui5 (>= 4.97.0)
  Depends: libkf5configwidgets5 (>= 4.96.0)
  Depends: libkf5coreaddons5 (>= 5.2.0)
  Depends: libkf5guiaddons5 (>= 4.96.0)
  Depends: libkf5i18n5 (>= 4.97.0)
  Depends: libkf5notifications5 (>= 4.96.0)
  Depends: libkf5widgetsaddons5 (>= 4.96.0)
  Depends: libkf5xmlgui-bin
  Depends: libkf5xmlgui5 (>= 4.98.0)
[B]  Depends: libqt5core5a (>= 5.11.0~rc1)
 |Depends: libqt5gui5 (>= 5.6.1~)
  Depends: libqt5gui5-gles (>= 5.6.1~)
  Depends: libqt5widgets5 (>= 5.6.1~)
  Depends: libqt5xml5 (>= 5.6.1~)[/B]
  Depends: libstdc++6 (>= 4.1.1)
  Breaks: kde-l10n-ar (<< 4:17.03.90-0~)
....
```

The Kcalc is dependent on KDE and Qt in the same time. KDE dependency packages are dependent on Qt, thus Kcalc depends on Qt.[B] 

Question: [/B]Due to the dependency of KDE on Qt, KDE cannot be removed (Qt as well). Can you confirm?

---

### Post by cruzer001 on 2019-06-07
Instead of removing packages I would op not to install everything.
```
sudo apt install --no-install-recommends lubuntu-desktop
```
[https://packages.ubuntu.com/disco/lubuntu-desktop](https://packages.ubuntu.com/disco/lubuntu-desktop)

Or a bare-bones install of lxqt and build from there.
[https://packages.ubuntu.com/disco/lxqt-core](https://packages.ubuntu.com/disco/lxqt-core)

---

### Post by Dennis N on 2019-06-07
Yes, Lubuntu has a few gnome packages. But that's not the same has having Gnome (Dekstop) installed. As to gnome-keyring, many distros utilize gnome-keyring - they don't make their own keyring application.

As you correctly state, **rdepends gnome-keyring** shows packages that depend on gnome keyring, but gnome keyring does not necessarily depend on them. So you can't conclude ubuntu-budgie-desktop is installed from this result. You must look further:

If you run this from Lubuntu 19.04, it will inform you if a package is installed or not:
```

dmn@Tyana-vm:~$ apt-cache policy ubuntu-budgie-desktop
ubuntu-budgie-desktop:
  [COLOR="#FF0000"]Installed: (none)[/COLOR]
  Candidate: 0.45
  Version table:
     0.45 500
        500 http://mirror.math.ucdavis.edu/ubuntu disco/universe amd64 Packages

```


As to KDE packages, KDE and Lubuntu 19.04 both use Qt, so they will have quite a few common libraries.

---

### Post by &amp;wP*!) on 2019-06-09
**cruzer001**, **Dennis N**, thanks for your help.

For information purpose: [This thread]("https://askubuntu.com/questions/351085/how-to-remove-recommended-and-suggested-dependencies-of-uninstalled-packages") and [Managing automatically installed packages]("https://www.debian.org/doc/manuals/aptitude/ch02s02s06.en.html") (at Debian site) explain how to remove suggested/recommended packages and keep Depends. Following command is helpful to find out which packages could be removed:
```
sudo apt-get autoremove -o APT::Autoremove::RecommendsImportant=0 -o APT::Autoremove::SuggestsImportant=0 --dry-run
```
Beware the last option. It does not let Autoremove delete the packages. 

This command should be used with care because some of them might be important.

---

