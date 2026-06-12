---
title: "How to install Xubuntu Desktop without downloading the extra packages?"
date: 2014-11-26
forum: Desktop Environments
---

### Post by flaymond on 2014-11-26
Hello, after fixing my pc pc problem..I guest wanna try ( I never tried that environment) Xubuntu without actually reinstall my OS back....is there any way to use and install Xubuntu environment without getting the default packages (just wanna replace Lubuntu with Xubuntu environment). If i succeed in install and using it....how to uninstall and switch back to Lubuntu and also delete the Xubuntu environment that i just installed (I wanna try first). Thanks for advance!

---

### Post by amanchesterman on 2014-11-26
I suggest that you get a memory stick (or CD if you prefer), download Xubuntu and create a live installer. Then boot your machine to **try** (not install) Xubuntu. That way you don't risk messing up your Lubuntu install and you get the full Xubuntu desktop experience. It will run more slowly than your Lubuntu because it's reading from the memory stick or CD but at least you will be able to try out all the features.

---

### Post by slickymaster on 2014-11-26
To install the basic software needed to run Xubuntu, but none of the Recommends: like Abiword, Gnumeric, Thunderbird, blueman, gmusicbrowser, etc., and their dependencies, ran:```
sudo apt-get install --no-install-recommends xubuntu-desktop
```

If you want too see what you'll be adding to your system before running the above command, ran:```
apt-cache show xubuntu-desktop | grep "Depends"
```On the other hand, if you want to see what you won't be adding, ran:```
apt-cache show xubuntu-desktop | grep "Recommends"
```

---

### Post by flaymond on 2014-11-26
Thanks for replies **_slick_**_**ymaster **_ and 	[**[COLOR=#000000]amanchesterman[/COLOR]**]("http://ubuntuforums.org/member.php?u=904255") 	 . 

- amanchesterman -- I don't like to use that method because my slow internet connection. Of course, I know how to install the XFCE environment with using terminal, but I don't know how to download only the needed package to run Xfce (I got lXDE and Cinnamon,  just wanna add my collections). But, your method can be used to others with a fast Internet Connections :)

- slickymaster -- Thanks for the detailed answer, and it was really nice to know what it will install and what it won't. So far, I wanna know how to uninstall the Xfce using terminal line? (In case I don't really like it and don't wanna heavy up my memory)

---

### Post by slickymaster on 2014-11-26
> **InterProg said:**
> <---snip--->
- slickymaster -- Thanks for the detailed answer, and it was really nice to know what it will install and what it won't. So far, I wanna know how to uninstall the Xfce using terminal line? (In case I don't really like it and don't wanna heavy up my memory)

Be aware that installing **xubuntu-desktop** isn't the same thing as installing **Xfce4**. When you install Xfce4, you get the standard Xfce4 desktop environment, however when you install xubuntu-desktop you get Xubuntu’s customized Xfce4 desktop environment instead.

The Xubuntu Desktop is a custom configured version of the Xfce4 Desktop. Xfce4 is smaller in terms of footprint than Xubuntu Core Desktop.

---

### Post by flaymond on 2014-11-26
Owh...so how I uninstalled it then...I found that using some sudo commands and removes abiword etc. But it dangerous for me because im using Abiword or I need to install Libreoffice to replace Abiword? or is there any way to uninstall it...without delete my already have softwares?

---

### Post by slickymaster on 2014-11-26
> **InterProg said:**
> Owh...so how I uninstalled it then...I found that using some sudo commands and removes abiword etc. But it dangerous for me because im using Abiword or I need to install Libreoffice to replace Abiword? or is there any way to uninstall it...without delete my already have softwares?

Uninstall what, specifically? Xubuntu Core Desktop or Xfce4?

---

### Post by flaymond on 2014-11-26
uninstall the Xubuntu Core Desktop (the code that you were give me).

---

### Post by slickymaster on 2014-11-26
Those are the packages that you'd be installing (plus their dependencies):```
~$ apt-cache show xubuntu-desktop | grep "Depends"
Depends: alsa-base, alsa-utils, anacron, bc, ca-certificates, dmz-cursor-theme, doc-base, fonts-dejavu-core, fonts-freefont-ttf, foomatic-db-compressed-ppds, genisoimage, ghostscript-x, gtk2-engines-pixbuf, inputattach, language-selector-gnome, libasound2-plugins, libpam-systemd, libsasl2-modules, libxp6, lightdm, lightdm-gtk-greeter, memtest86+, openprinting-ppds, pm-utils, printer-driver-pnm2ppa, rfkill, software-properties-gtk, thunar, thunar-volman, tumbler, ubuntu-drivers-common, ubuntu-extras-keyring, unzip, update-manager, wireless-tools, wpasupplicant, xdg-user-dirs, xdg-user-dirs-gtk, xfce4-appfinder, xfce4-notifyd, xfce4-panel, xfce4-session, xfce4-settings, xfdesktop4, xfwm4, xkb-data, xorg, xterm, xubuntu-artwork, xubuntu-default-settings, zenity, zip
```

This is just a simulation install on a Lubuntu 14.10 box```
~$ sudo apt-get install -s --no-install-recommends xubuntu-desktop 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  bluebird-gtk-theme doc-base exo-utils greybird-gtk-theme libgarcon-1-0
  libgarcon-common libthunarx-2-0 libtumbler-1-0 libuuid-perl
  libyaml-tiny-perl numix-gtk-theme orion-gtk-theme shimmer-themes thunar
  thunar-data thunar-volman tumbler tumbler-common xfce4-appfinder xfce4-panel
  xfce4-session xfce4-settings xfdesktop4 xfdesktop4-data xfwm4
  xubuntu-artwork xubuntu-default-settings
Suggested packages:
  dhelp dwww doc-central yelp khelpcenter4 rarian-compat albatross-gtk-theme
  shimmer-wallpapers thunar-archive-plugin thunar-media-tags-plugin
  tumbler-plugins-extra fortunes-mod menu xfce4 xfwm4-themes
Recommended packages:
  xfce4-volumed xubuntu-icon-theme plymouth-theme-xubuntu-logo
  plymouth-theme-xubuntu-text xubuntu-wallpapers libxfce4ui-utils
  abiword-plugin-grammar abiword-plugin-mathview acpi-support
  app-install-data-partner apt-offline avahi-autoipd bluez-alsa bluez-cups
  brltty brltty-x11 catfish cups-bsd espeak fonts-kacst-one fonts-khmeros-core
  fonts-lao fonts-lklug-sinhala fonts-opensymbol fonts-sil-abyssinica
  fonts-sil-padauk fonts-takao-pgothic fonts-thai-tlwg fonts-tibetan-machine
  gigolo gimp gmusicbrowser gnome-calculator gnome-mines gnome-sudoku
  gstreamer0.10-plugins-base-apps gstreamer0.10-pulseaudio gtk-theme-config
  hplip indicator-messages indicator-sound inxi kerneloops-daemon
  libnotify-bin libpam-gnome-keyring menulibre mousepad mugshot
  network-manager-pptp network-manager-pptp-gnome onboard orage parole
  pastebinit pavucontrol pcmciautils pidgin-otr printer-driver-brlaser
  printer-driver-c2esp printer-driver-foo2zjs printer-driver-min12xxw
  printer-driver-ptouch printer-driver-pxljr printer-driver-sag-gdi
  printer-driver-splix ristretto software-center speech-dispatcher thunderbird
  ttf-indic-fonts-core ttf-punjabi-fonts xcursor-themes xfce4-cpugraph-plugin
  xfce4-dict xfce4-indicator-plugin xfce4-mailwatch-plugin
  xfce4-netload-plugin xfce4-notes-plugin xfce4-places-plugin
  xfce4-quicklauncher-plugin xfce4-screenshooter xfce4-systemload-plugin
  xfce4-taskmanager xfce4-terminal xfce4-verve-plugin xfce4-weather-plugin
  xfce4-whiskermenu-plugin xfce4-xkb-plugin xubuntu-community-wallpapers
  xubuntu-docs
The following NEW packages will be installed:
  bluebird-gtk-theme doc-base exo-utils greybird-gtk-theme libgarcon-1-0
  libgarcon-common libthunarx-2-0 libtumbler-1-0 libuuid-perl
  libyaml-tiny-perl numix-gtk-theme orion-gtk-theme shimmer-themes thunar
  thunar-data thunar-volman tumbler tumbler-common xfce4-appfinder xfce4-panel
  xfce4-session xfce4-settings xfdesktop4 xfdesktop4-data xfwm4
  xubuntu-artwork xubuntu-default-settings xubuntu-desktop
0 upgraded, 28 newly installed, 0 to remove and 3 not upgraded.
Inst libgarcon-common (0.3.0-1ubuntu2 Ubuntu:14.10/utopic [all])
Inst libgarcon-1-0 (0.3.0-1ubuntu2 Ubuntu:14.10/utopic [i386])
Inst thunar-data (1.6.3-1ubuntu6 Ubuntu:14.10/utopic-updates [all])
Inst libthunarx-2-0 (1.6.3-1ubuntu6 Ubuntu:14.10/utopic-updates [i386])
Inst libtumbler-1-0 (0.1.30-1ubuntu2 Ubuntu:14.10/utopic [i386])
Inst exo-utils (0.10.2-4 Ubuntu:14.10/utopic [i386])
Inst xfce4-panel (4.11.1-0ubuntu2 Ubuntu:14.10/utopic [i386])
Inst xfce4-settings (4.11.3-0ubuntu2 Ubuntu:14.10/utopic [i386])
Inst xfce4-session (4.11.0-1ubuntu1 Ubuntu:14.10/utopic [i386])
Inst bluebird-gtk-theme (1.8.1-0ubuntu1 Ubuntu:14.10/utopic [all])
Inst libuuid-perl (0.05-1build1 Ubuntu:14.10/utopic [i386])
Inst libyaml-tiny-perl (1.63-1 Ubuntu:14.10/utopic [all])
Inst doc-base (0.10.6 Ubuntu:14.10/utopic [all])
Inst greybird-gtk-theme (1.8.1-0ubuntu1 Ubuntu:14.10/utopic [all])
Inst numix-gtk-theme (1.8.1-0ubuntu1 Ubuntu:14.10/utopic [all])
Inst orion-gtk-theme (1.8.1-0ubuntu1 Ubuntu:14.10/utopic [all])
Inst shimmer-themes (1.8.1-0ubuntu1 Ubuntu:14.10/utopic [all])
Inst thunar (1.6.3-1ubuntu6 Ubuntu:14.10/utopic-updates [i386])
Inst thunar-volman (0.8.0-4ubuntu1 Ubuntu:14.10/utopic [i386])
Inst tumbler-common (0.1.30-1ubuntu2 Ubuntu:14.10/utopic [all])
Inst tumbler (0.1.30-1ubuntu2 Ubuntu:14.10/utopic [i386])
Inst xfce4-appfinder (4.11.0-1 Ubuntu:14.10/utopic [i386])
Inst xfdesktop4-data (4.11.8-0ubuntu1 Ubuntu:14.10/utopic [all])
Inst xfdesktop4 (4.11.8-0ubuntu1 Ubuntu:14.10/utopic [i386])
Inst xfwm4 (4.11.2-0ubuntu2 Ubuntu:14.10/utopic [i386])
Inst xubuntu-artwork (14.10.3 Ubuntu:14.10/utopic [all])
Inst xubuntu-default-settings (14.10.11 Ubuntu:14.10/utopic [all])
Inst xubuntu-desktop (2.184 Ubuntu:14.10/utopic [i386])
Conf libgarcon-common (0.3.0-1ubuntu2 Ubuntu:14.10/utopic [all])
Conf libgarcon-1-0 (0.3.0-1ubuntu2 Ubuntu:14.10/utopic [i386])
Conf thunar-data (1.6.3-1ubuntu6 Ubuntu:14.10/utopic-updates [all])
Conf libthunarx-2-0 (1.6.3-1ubuntu6 Ubuntu:14.10/utopic-updates [i386])
Conf libtumbler-1-0 (0.1.30-1ubuntu2 Ubuntu:14.10/utopic [i386])
Conf exo-utils (0.10.2-4 Ubuntu:14.10/utopic [i386])
Conf xfce4-panel (4.11.1-0ubuntu2 Ubuntu:14.10/utopic [i386])
Conf xfce4-settings (4.11.3-0ubuntu2 Ubuntu:14.10/utopic [i386])
Conf xfce4-session (4.11.0-1ubuntu1 Ubuntu:14.10/utopic [i386])
Conf bluebird-gtk-theme (1.8.1-0ubuntu1 Ubuntu:14.10/utopic [all])
Conf libuuid-perl (0.05-1build1 Ubuntu:14.10/utopic [i386])
Conf libyaml-tiny-perl (1.63-1 Ubuntu:14.10/utopic [all])
Conf doc-base (0.10.6 Ubuntu:14.10/utopic [all])
Conf greybird-gtk-theme (1.8.1-0ubuntu1 Ubuntu:14.10/utopic [all])
Conf numix-gtk-theme (1.8.1-0ubuntu1 Ubuntu:14.10/utopic [all])
Conf orion-gtk-theme (1.8.1-0ubuntu1 Ubuntu:14.10/utopic [all])
Conf shimmer-themes (1.8.1-0ubuntu1 Ubuntu:14.10/utopic [all])
Conf thunar (1.6.3-1ubuntu6 Ubuntu:14.10/utopic-updates [i386])
Conf thunar-volman (0.8.0-4ubuntu1 Ubuntu:14.10/utopic [i386])
Conf tumbler-common (0.1.30-1ubuntu2 Ubuntu:14.10/utopic [all])
Conf tumbler (0.1.30-1ubuntu2 Ubuntu:14.10/utopic [i386])
Conf xfce4-appfinder (4.11.0-1 Ubuntu:14.10/utopic [i386])
Conf xfdesktop4-data (4.11.8-0ubuntu1 Ubuntu:14.10/utopic [all])
Conf xfdesktop4 (4.11.8-0ubuntu1 Ubuntu:14.10/utopic [i386])
Conf xfwm4 (4.11.2-0ubuntu2 Ubuntu:14.10/utopic [i386])
Conf xubuntu-artwork (14.10.3 Ubuntu:14.10/utopic [all])
Conf xubuntu-default-settings (14.10.11 Ubuntu:14.10/utopic [all])
Conf xubuntu-desktop (2.184 Ubuntu:14.10/utopic [i386])
```

But there's a catch when it comes to uninstalling, because there are quite a few packages that are common to Xubuntu and Lubuntu and you'd have to be extremely careful with what you'd be removing.

---

### Post by sudodus on 2014-11-26
If you have enough space on your internal disk, it is a good idea to have one production system (I recommend an LTS version so 12.04.5 or 14.04.1 right now) and one or more testing systems in their own partition(s), where you can take risks, and learn what is happening when you test the limits :-)

If you want to test really risky things, it is a good idea to do it in virtual machines (for example VirtualBox or KVM and virt-manager). Then there is a very low risk for the computer's hardware and operating system (the host system of the virtual machine). But you need a fairly powerful computer (CPU and RAM) in order to run a virtual machine compared to running directly in the hardware.

-o-

Finally you should always have a good backup of at least your personal data (pictures, documents, video clips etc). Keep the backup separate from the computer except when backing up. "Tough guys never backup their data, they do the work twice instead" ;-)

---

### Post by slickymaster on 2014-11-26
> **sudodus said:**
> If you have enough space on your internal disk, it is a good idea to have one production system (I recommend an LTS version so 12.04.5 or 14.04.1 right now) and one or more testing systems in their own partition(s), where you can take risks, and learn what is happening when you test the limits :-)

If you want to test really risky things, it is a good idea to do it in virtual machines (for example VirtualBox or KVM and virt-manager). Then there is a very low risk for the computer's hardware and operating system (the host system of the virtual machine). But you need a fairly powerful computer (CPU and RAM) in order to run a virtual machine compared to running directly in the hardware.

-o-

Finally you should always have a good backup of at least your personal data (pictures, documents, video clips etc). Keep the backup separate from the computer except when backing up. "Tough guys never backup their data, they do the work twice instead" ;-)

I can't +1 enough sudodus advice.

---

### Post by flaymond on 2014-11-27
thanks for help!

Thanks for the advice Sudodus.

---

