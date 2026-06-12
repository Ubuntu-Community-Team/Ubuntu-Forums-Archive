---
title: "Installed KDE, want to uninstall it"
date: 2010-10-14
forum: Desktop Environments
---

### Post by nintendude794 on 2010-10-14
So I installed KDE and after playing with it a dozen or two minutes, I wanna get rid of it and every package associated with it.  How do I do this?

P.S.: I used this command in terminal:
```
$ sudo aptitude install kubuntu-desktop
```

---

### Post by garvinrick4 on 2010-10-14
```
rick@rick-laptop:~$ aptitude show kubuntu-desktop
Package: kubuntu-desktop                 
State: not installed
Version: 1.205
Priority: optional
Section: metapackages
Maintainer: Kubuntu Developers <kubuntu-devel@lists.ubuntu.com>
Uncompressed Size: 57.3k
Depends: alsa-base, alsa-utils, anacron, ark, bc, ca-certificates, cups,
         cups-bsd, cups-client, dc, dolphin, foomatic-db-compressed-ppds,
         foomatic-filters, genisoimage, ghostscript-x, hal, inputattach,
         kde-window-manager, kde-zeroconf, kdebase-workspace-bin,
         kdemultimedia-kio-plugins, kdepasswd, kdm, khelpcenter4, klipper, kmix,
         konsole, ksnapshot, ksysguard, kubuntu-netbook-default-settings,
         language-selector-qt, lftp, libpam-ck-connector, libsasl2-modules,
         libxp6, okular, openprinting-ppds, phonon-backend-xine, plasma-desktop,
         plasma-netbook, pnm2ppa, screen, smbclient, software-properties-kde,
         systemsettings, ttf-dejavu-core, ttf-freefont, ubuntu-extras-keyring,
         unzip, wireless-tools, wpasupplicant, x-ttcidfont-conf, xdg-user-dirs,
         xkb-data, xorg, zip
Recommends: acpi-support, akregator, amarok, apport-kde, apturl-kde,
            avahi-autoipd, avahi-daemon, bluedevil, bluez, bluez-alsa,
            bluez-cups, brltty, cdrdao, dragonplayer, foo2zjs, gdebi-kde,
            gnupg-agent, gtk2-engines-qtcurve, gwenview, hplip, ibus-qt4,
            im-switch, jockey-kde, k3b, kaddressbook, kamera, kate, kcalc,
            kde-config-gtk, kde-config-touchpad, kdegraphics-strigi-plugins,
            kdepim-kresources, kdepim-runtime, kdepim-strigi-plugins,
            kdepim-wizards, kdesudo, kerneloops-daemon, kmag, kmail, kmousetool,
            knotes, kontact, kopete, korganizer, kpackagekit, kppp, ksystemlog,
            ktorrent, kubuntu-default-settings, kubuntu-docs,
            kubuntu-firefox-installer, kubuntu-konqueror-shortcuts,
            kubuntu-notification-helper, kvkbd, kwalletmanager, laptop-detect,
            libnss-mdns, libqca2-plugin-ossl, min12xxw,
            network-manager-pptp-kde, okular-extra-backends,
            openoffice.org-calc, openoffice.org-impress, openoffice.org-kde,
            openoffice.org-style-oxygen, openoffice.org-writer,
            oxygen-cursor-theme, oxygen-icon-theme, pcmciautils, pinentry-qt4,
            plasma-widget-facebook, plasma-widget-folderview,
            plasma-widget-kimpanel, plasma-widget-kubuntu-feedback,
            plasma-widget-menubar, plasma-widget-message-indicator,
            plasma-widget-networkmanagement, plasma-widget-quickaccess,
            plasma-widgets-addons, plymouth-theme-kubuntu-logo,
            plymouth-theme-kubuntu-text, policykit-desktop-privileges,
            printer-applet, pulseaudio, pulseaudio-module-bluetooth, pxljr,
            quassel, rekonq, splix, system-config-printer-kde,
            ttf-indic-fonts-core, ttf-kacst-one, ttf-khmeros-core, ttf-lao,
            ttf-liberation, ttf-punjabi-fonts, ttf-takao-pgothic, ttf-thai-tlwg,
            ttf-ubuntu-font-family, ttf-unfonts-core, ttf-wqy-microhei,
            usb-creator-kde, userconfig, xcursor-themes, xdg-utils
Conflicts: kubuntu-kde4-desktop
Replaces: kubuntu-kde4-desktop
Provides: kubuntu-kde4-desktop
Description: Kubuntu Plasma Desktop system
 This package depends on all of the packages in the Kubuntu desktop system.
 Installing this package will include the default Kubuntu Plasma Desktop
 installation. It is safe to remove this package if some of the desktop system
 packages are not desired.

[CODE]sudo apt-get remove kubuntu-desktop
``` 
[/CODE]

---

### Post by inobe on 2010-10-14
you are sooo lucky you used the aptitude command because now you can completely remove all the packages associated with kde desktop.


```
sudo apt-get autoremove kubuntu-desktop
```

other ways

```
sudo aptitude remove kubuntu-desktop
```

---

### Post by nintendude794 on 2010-10-14
OH NOES
```
hunter@hunter-laptop:~$ aptitude show kubuntu-desktop
Package: kubuntu-desktop                 
State: installed
Automatically installed: no
Version: 1.205
Priority: optional
Section: metapackages
Maintainer: Kubuntu Developers <kubuntu-devel@lists.ubuntu.com>
Uncompressed Size: 57.3k
Depends: alsa-base, alsa-utils, anacron, ark, bc, ca-certificates, cups,
         cups-bsd, cups-client, dc, dolphin, foomatic-db-compressed-ppds,
         foomatic-filters, genisoimage, ghostscript-x, hal, inputattach,
         kde-window-manager, kde-zeroconf, kdebase-workspace-bin,
         kdemultimedia-kio-plugins, kdepasswd, kdm, khelpcenter4, klipper, kmix,
         konsole, ksnapshot, ksysguard, kubuntu-netbook-default-settings,
         language-selector-qt, lftp, libpam-ck-connector, libsasl2-modules,
         libxp6, okular, openprinting-ppds, phonon-backend-xine, plasma-desktop,
         plasma-netbook, pnm2ppa, screen, smbclient, software-properties-kde,
         systemsettings, ttf-dejavu-core, ttf-freefont, ubuntu-extras-keyring,
         unzip, wireless-tools, wpasupplicant, x-ttcidfont-conf, xdg-user-dirs,
         xkb-data, xorg, zip
Recommends: acpi-support, akregator, amarok, apport-kde, apturl-kde,
            avahi-autoipd, avahi-daemon, bluedevil, bluez, bluez-alsa,
            bluez-cups, brltty, cdrdao, dragonplayer, foo2zjs, gdebi-kde,
            gnupg-agent, gtk2-engines-qtcurve, gwenview, hplip, ibus-qt4,
            im-switch, jockey-kde, k3b, kaddressbook, kamera, kate, kcalc,
            kde-config-gtk, kde-config-touchpad, kdegraphics-strigi-plugins,
            kdepim-kresources, kdepim-runtime, kdepim-strigi-plugins,
            kdepim-wizards, kdesudo, kerneloops-daemon, kmag, kmail, kmousetool,
            knotes, kontact, kopete, korganizer, kpackagekit, kppp, krdc, krfb,
            ksystemlog, ktimetracker, ktorrent, kubuntu-default-settings,
            kubuntu-docs, kubuntu-firefox-installer,
            kubuntu-konqueror-shortcuts, kubuntu-notification-helper, kvkbd,
            kwalletmanager, laptop-detect, libnss-mdns, libqca2-plugin-ossl,
            min12xxw, network-manager-pptp-kde, okular-extra-backends,
            openoffice.org-calc, openoffice.org-impress, openoffice.org-kde,
            openoffice.org-style-oxygen, openoffice.org-writer,
            oxygen-cursor-theme, oxygen-icon-theme, oxygen-icon-theme-complete,
            pcmciautils, pinentry-qt4, plasma-widget-facebook,
            plasma-widget-folderview, plasma-widget-kimpanel,
            plasma-widget-kubuntu-feedback, plasma-widget-menubar,
            plasma-widget-message-indicator, plasma-widget-networkmanagement,
            plasma-widget-quickaccess, plasma-widgets-addons,
            plymouth-theme-kubuntu-logo, plymouth-theme-kubuntu-text,
            policykit-desktop-privileges, printer-applet, pulseaudio,
            pulseaudio-module-bluetooth, pxljr, quassel, rdesktop, rekonq,
            splix, system-config-printer-kde, ttf-indic-fonts-core,
            ttf-kacst-one, ttf-khmeros-core, ttf-lao, ttf-liberation,
            ttf-punjabi-fonts, ttf-takao-pgothic, ttf-thai-tlwg,
            ttf-ubuntu-font-family, ttf-unfonts-core, ttf-wqy-microhei,
            usb-creator-kde, userconfig, xcursor-themes, xdg-utils
Conflicts: kubuntu-kde4-desktop
Replaces: kubuntu-kde4-desktop
Provides: kubuntu-kde4-desktop
Description: Kubuntu Plasma Desktop system
 This package depends on all of the packages in the Kubuntu desktop system.
 Installing this package will include the default Kubuntu Plasma Desktop
 installation. It is safe to remove this package if some of the desktop system
 packages are not desired.

hunter@hunter-laptop:~$ sudo apt-get remove kubuntu-desktop
[sudo] password for hunter: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  amarok-common libtag-extras1 liblastfm0 amarok-utils
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  kubuntu-desktop
0 upgraded, 0 newly installed, 1 to remove and 1 not upgraded.
After this operation, 57.3kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 148822 files and directories currently installed.)
Removing kubuntu-desktop ...
hunter@hunter-laptop:~$ sudo apt-get autoremove kubuntu-desktop
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package kubuntu-desktop is not installed, so not removed
The following packages will be REMOVED:
  amarok-common amarok-utils liblastfm0 libtag-extras1
0 upgraded, 0 newly installed, 4 to remove and 1 not upgraded.
After this operation, 7,524kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 148819 files and directories currently installed.)
Removing amarok-common ...
Removing amarok-utils ...
Removing liblastfm0 ...
Removing libtag-extras1 ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for man-db ...
/usr/bin/mandb: can't write to /var/cache/man/3878: No space left on device
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place

```

---

### Post by inobe on 2010-10-14
> **nintendude794 said:**
> Thanks, both o' y'all! :)

it should, it's been a year since personally tried, it worked well then.

if things go wrong and ubuntu-desktop is in shambles hitting escape during boot up will give you some options, you want root shell then enter this

```
sudo apt-get install ubuntu-desktop
```


that will reinstall ubuntu desktop.

backup your stuff, make sure you have a live cd encase you it completely fails.

---

### Post by nintendude794 on 2010-10-14
> **inobe said:**
> it should, it's been a year since personally tried, it worked well then.

if things go wrong and ubuntu-desktop is in shambles hitting escape during boot up will give you some options, you want root shell then enter this

```
sudo apt-get install ubuntu-desktop
```


that will reinstall ubuntu desktop.

backup your stuff, make sure you have a live cd encase you it completely fails.

Ubuntu Desktop is still workin' fine.  That command jus' didn't get rid of much.  Still got some random software that KDE uses and I don't.

---

### Post by inobe on 2010-10-14
> **nintendude794 said:**
> Ubuntu Desktop is still workin' fine.  That command jus' didn't get rid of much.  Still got some random software that KDE uses and I don't.

it's encase something goes wrong and ubuntu breaks, if not broken leave well enough alone :P

---

### Post by nintendude794 on 2010-10-14
> **inobe said:**
> it's encase something goes wrong and ubuntu breaks, if not broken leave well enough alone :P

With only 8MBs remaining on this 5GB partition of my MacBook....500MBs is kinda valuable.

---

### Post by inobe on 2010-10-14
> **nintendude794 said:**
> With only 8MBs remaining on this 5GB partition of my MacBook....500MBs is kinda valuable.

cool, now refer back to post three and look at the command you used in post 4 ?

---

### Post by inobe on 2010-10-14
before this gets out of hand, use the first command from post 3, if it wants to remove 3megs hit **n** for No then try the aptitude command instead :P

---

### Post by nintendude794 on 2010-10-14
> **inobe said:**
> cool, now refer back to post three and look at the command you used in post 4 ?

Post 4 shows a few commands, which one?

---

### Post by nintendude794 on 2010-10-14
> **inobe said:**
> before this gets out of hand, use the first command from post 3, if it wants to remove 3megs hit **n** for No then try the aptitude command instead :P

Hmm... say what? lol

---

### Post by inobe on 2010-10-14
> **nintendude794 said:**
> Hmm... say what? lol

just like that, run the first command, if it shows in terminal that it wants to remove a small portion, try the last command and see if any difference.

we know for a fact that kubuntu desktop is well over 100megs+


basically don't type "y" if you know the command won't work because then you will just make a mess :P

---

### Post by nintendude794 on 2010-10-14
> **inobe said:**
> just like that, run the first command, if it shows in terminal that it wants to remove a small portion, try the last command and see if any difference.

we know for a fact that kubuntu desktop is well over 100megs+


basically don't type "y" if you know the command won't work because then you will just make a mess :P

```
hunter@hunter-laptop:~$ sudo aptitude remove kubuntu-desktop
[sudo] password for hunter: 
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
                                         
hunter@hunter-laptop:~$ sudo apt-get autoremove kubuntu-desktop
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package kubuntu-desktop is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
hunter@hunter-laptop:~$ 

```

---

### Post by inobe on 2010-10-14
> **nintendude794 said:**
> ```
hunter@hunter-laptop:~$ sudo aptitude remove kubuntu-desktop
[sudo] password for hunter: 
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
                                         
hunter@hunter-laptop:~$ sudo apt-get autoremove kubuntu-desktop
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package kubuntu-desktop is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
hunter@hunter-laptop:~$ 

```


the command you used in post 4 may be the culprit, it possibly removed essential files that the commands i posted needed.

you may need to reinstall those packages or reinstall kubuntu desktop and try again.

or you can try this [http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

please read before you proceed and use the kubuntu command, and be sure to highlight the entire command before pasting in terminal.

remember the command to reinstall ubuntu if things go terribly wrong.

---

