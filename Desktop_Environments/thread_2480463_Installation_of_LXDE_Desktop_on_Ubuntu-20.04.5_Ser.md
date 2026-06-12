---
title: "Installation of LXDE Desktop on Ubuntu-20.04.5 Server"
date: 2022-10-31
forum: Desktop Environments
---

### Post by fljarvis on 2022-10-31
[LEFT] [FONT=Tinos]**There have been several subject-related articles on the web describing a**[/FONT]             
[/LEFT]
             [LEFT] [FONT=Tinos]**simple, essentially 2 step approach for the installation:**[/FONT]             [/LEFT]
             [LEFT] [FONT=Tinos]** i) install a display manager, eg.   sudo apt install lightdm**[/FONT]             [/LEFT]
             [LEFT] [FONT=Tinos][B]ii) install LXDE and reboot,  sudo apt install LXDE,  sudo reboot
[/B][/FONT]
[/LEFT]
                          [LEFT] [FONT=Tinos]**Unfortunately, this does not work well on the Ubuntu-20.04.5 Server**[/FONT]             [/LEFT]
             [LEFT] [FONT=Tinos]**because, in addition to installing LXDE, an entire Gnome desktop**[/FONT]             [/LEFT]
             [LEFT] [FONT=Tinos]**environment is installed as well.  A more detailed installation approach**[/FONT]             [/LEFT]
             [LEFT] [FONT=Tinos]**is required to achieve the LXDE installation, but omit the Gnome desktop**[/FONT]             [/LEFT]
             [LEFT] [FONT=Tinos]**environment.**[/FONT]             [/LEFT]
                          [LEFT] [FONT=Tinos]**********************************************************************************[/FONT]             [/LEFT]
             [LEFT] [FONT=Tinos]**Extra Software Uploads**[/FONT]             [/LEFT]
                          [LEFT] [FONT=Tinos]**Because the Ubuntu server has no GUI,  extra software is imported from a USB stick, sudo mount /dev/db1 /mnt.**[/FONT]             [/LEFT]
             [LEFT] [FONT=Tinos]**********************************************************************************[/FONT]             [/LEFT]
             [LEFT] [FONT=Tinos][B]Installation Steps
[/B][/FONT]
[/LEFT]
                          [LEFT] [FONT=Tinos]**  i)  sudo apt install lightdm-gtk-greeter,       install 80 packages.**[/FONT]             [/LEFT]
             [LEFT] [FONT=Tinos]**      This avoids the installation of the default Unity-greeter, which**[/FONT]             [/LEFT]
             [LEFT] [FONT=Tinos][B]      would trigger the entire Gnome desktop installation.
[/B][/FONT]
[/LEFT]
                          [LEFT] [FONT=Tinos]** ii)  sudo apt install lightdm,         installs  63  packages.**[/FONT]             [/LEFT]
                          [LEFT] [FONT=Tinos]**       After this step, any normal reboots bring up the lightdm login screen,**[/FONT]             [/LEFT]
             [LEFT] [FONT=Tinos]**       but there is no xsession available at this point in which to login.**[/FONT]             [/LEFT]
             [LEFT] [FONT=Tinos]**       Therefore, until LXDE is finally installed, all reboots involve selecting**[/FONT]             [/LEFT]
             [LEFT] [FONT=Tinos]**       the Advanced Options grub entry, and appending a blank-3 to the**[/FONT]             [/LEFT]
             [LEFT] [FONT=Tinos][B]       linux /vmlinuz line followed by cntrl-x to force a command-line login.
[/B][/FONT]
[/LEFT]
                          [LEFT] [FONT=Tinos]**iii)   upload 7 bionic packages into a local directory and install them in**[/FONT]             [/LEFT]
             [LEFT] [FONT=Tinos]**       the following manner:**[/FONT]             [/LEFT]
                          [LEFT] [FONT=Tinos]**      -sudo apt install ./leafpad*.deb**[/FONT]             [/LEFT]
             [LEFT] [FONT=Tinos]**      -sudo apt install ./python-glade2*.deb ./python-gtk2*.deb,**[/FONT]             [/LEFT]
             [LEFT] [FONT=Tinos]**             installs 12 packages**[/FONT]             [/LEFT]
             [LEFT] [FONT=Tinos]**      -sudo apt install ./wicd-1*.deb ./wicd-daemon*.deb ./wicd-gtk*.deb**[/FONT]             [/LEFT]
             [LEFT] [FONT=Tinos][B]             ./python-wicd*.deb,        installs 14 packages
[/B][/FONT]
[/LEFT]
                          [LEFT] [FONT=Tinos]** iv)  sudo apt install lxpolkit,        installs 3 packages, including libunique**[/FONT]             [/LEFT]
             [LEFT] [FONT=Tinos][B]              and lxsession-data
[/B][/FONT]
[/LEFT]
                          [LEFT] [FONT=Tinos][B]  v)  sudo apt install gir1.2-polkit-1.0,    installs the polkit-1 framework
[/B][/FONT]
[/LEFT]
                          [LEFT] [FONT=Tinos]** vi)  sudo apt install lxde-session lxpanel pcmanfm lxterminal notification-**[/FONT]             [/LEFT]
             [LEFT] [FONT=Tinos]**               daemon xscreensaver,       installs 130 packages**[/FONT]             [/LEFT]
             [LEFT] [FONT=Tinos]**      Without trying to install the entire lxde-core metapackage,  install the**[/FONT]             [/LEFT]
             [LEFT] [FONT=Tinos][B]       remaining required un-installed components of the metapackage.
[/B][/FONT]
[/LEFT]
                          [LEFT] [FONT=Tinos][B]vii)  sudo apt install lxde,        installs 267 packages
[/B][/FONT]
[/LEFT]
                          [LEFT] [FONT=Tinos]**viii)  sudo reboot,        boot up in normal mode,   lxde session available**[/FONT]             [/LEFT]
                          [LEFT] [FONT=Tinos]*********************************************************************************[/FONT]             [/LEFT]
             [LEFT] [FONT=Tinos]**Len E.**[/FONT]             
[/LEFT]

---

### Post by ActionParsnip on 2022-10-31
LXDE is pretty dead. I suggest LXQT instead.

---

