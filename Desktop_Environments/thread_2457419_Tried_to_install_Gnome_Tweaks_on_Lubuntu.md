---
title: "Tried to install Gnome Tweaks on Lubuntu"
date: 2021-02-01
forum: Desktop Environments
---

### Post by username2758 on 2021-02-01
Hey,

What happens if I try and install Gnome Tweaks on Lubuntu which doesn't use Gnome?

Will it install the Gnome desktop environment?

I really did that because I thought I was on Ubuntu instead. 

:oops:

---

### Post by guiverc on 2021-02-01
You haven't said what release of Lubuntu you're talking about.

Legacy Lubuntu which uses LXDE/GTK2?

or 

Modern Lubuntu which uses LXQt/Qt5?

I have `gnome-tweaks` installed, but my Lubuntu (LXQt) desktop also has Ubuntu (GNOME) & Xubuntu (XFCE) installed, so the effect is minimal.

As I don't know your release, I'll provide my release's link of `gnome-tweaks` tool

[https://packages.ubuntu.com/hirsute/gnome-tweaks](https://packages.ubuntu.com/hirsute/gnome-tweaks)

You'll note some of GNOME is brought in, those packages may cause others to be brought in (gnome-tweaks does nothing for my current Lubuntu/LXQt desktop anyway, and I just ran it so it's sitting there.. but I see no point to it, given currently I'm using my Lubuntu (LXQt) desktop/session.  Changes made there will impact my GNOME experience more so, some can influence my current setup, but I'd not make changes using it, but using my LXQt tools instead (GNOME tools work great in gnome, LXQt tools work in better in my Lubuntu)

---

### Post by username2758 on 2021-02-02
Thanks. Sorry, it's Lubuntu with LXQt.

My goal was to install gnome-tweaks to be able to fiddle with font rendering settings, and forgot I wasn't using Ubuntu on this machine.

So I ended up installing gnome-tweaks and now I am given the option to start the session with Gnome and Wayland at the login screen.

How do I completely remove Gnome from the system now?

---

### Post by Frogs Hair on 2021-02-02
Dependencies for gnome-tweak include the entire gnome-desktop-environment. You can uninstall all of the packages via the synaptic-package-manager if you know which ones.  It would be much faster to backup and reinstall a Ubuntu flavor of your choice. Completely removing a second desktop environment is time  very consuming and may cause breakage.

---

### Post by username2758 on 2021-02-02
> **Frogs Hair said:**
> Dependencies for gnome-tweak include the entire gnome-desktop-environment. You can uninstall all of the packages via the synaptic-package-manager if you know which ones.  It would be much faster to backup and reinstall a Ubuntu flavor of your choice. Completely removing a second desktop environment is time  very consuming and may cause breakage.

Well I did try to remove Gnome anyway, but am not sure what was done exactly.

I used the following command, and Lubuntu on LXQt is working fine so far:

sudo apt-get remove ubuntu-gnome-desktop

But I'm not sure if that command deleted everything completely.

---

### Post by CelticWarrior on 2021-02-02
> **username2758 said:**
> Well I did try to remove Gnome anyway, but am not sure what was done exactly.

I used the following command, and Lubuntu on LXQt is working fine so far:

sudo apt-get remove ubuntu-gnome-desktop

But I'm not sure if that command deleted everything completely.

It removes nothing but itself because it's a meta-package, i.e., it contains information about other packages to install. As explained above you would need to manually uninstall all the packages that the meta-package tells the system to install.

---

### Post by Frogs Hair on 2021-02-02
Did that remove the gnome login options? Gnome brings a number of applications with it as well, but f you don't mind having a second DE or extra packages then leave it as is. below are the dependencies for gnome-tweak and there are more related packages.

---

### Post by username2758 on 2021-02-02
> **Frogs Hair said:**
> Did that remove the gnome login options? Gnome brings a number of applications with it as well, but f you don't mind having a second DE or extra packages then leave it as is. below are the dependencies for gnome-tweak and there are more related packages.

Yes that did remove the Gnome login options, but apparently I still have all the dependencies from your screenshot (thank you btw):

Like how big are these dependencies? I don't understand about Linux structure, and before I installed gnome-tweaks I did install some gnome software individually like System Monitor, Gedit, etc.

If I remove those packages from your screenshot, will it affect other software like System Monitor and Gedit?

Curiously, after I messed up trying to install gnome-tweaks when I logged in using Wayland there was nothing on screen, just the wallpaper. No taskbar, nothing.

---

### Post by Frogs Hair on 2021-02-02
It won't hurt anything to leave them installed, they just take up space.

---

### Post by username2758 on 2021-02-02
> **Frogs Hair said:**
> It won't hurt anything to leave them installed, they just take up space.

But is it too much space?

---

### Post by guiverc on 2021-02-02
Given you installed `gnome-tweaks`, and everything else was installed because of that, a simple removal of that package, followed by 

```
sudo apt autoremove
```

I would have expected would have removed almost everything.  Because the other packages were installed because they were requirements of the `gnome-tweaks` installation, they will be marked as such (or more aren't marked as manually installed), thus get remove with the `autoremove` IF they are no longer required.

If you have the disk space, and don't mind the extra bandwidth on updates (updates for your lubuntu & ubuntu desktops will occur, thus extra free space is required for updates to be downloaded & installed), I'd have left it; but I'm a multi-desktop person (like having a change by using a different desktop some days).

FYI:  *It's useful if we know your actual release details, the last five releases of Lubuntu have used LXQt so providing that allows us to be more precise.*

---

### Post by username2758 on 2021-02-02
> **guiverc said:**
> Given you installed `gnome-tweaks`, and everything else was installed because of that, a simple removal of that package, followed by 

```
sudo apt autoremove
```

I would have expected would have removed almost everything.  Because the other packages were installed because they were requirements of the `gnome-tweaks` installation, they will be marked as such (or more aren't marked as manually installed), thus get remove with the `autoremove` IF they are no longer required.

If you have the disk space, and don't mind the extra bandwidth on updates (updates for your lubuntu & ubuntu desktops will occur, thus extra free space is required for updates to be downloaded & installed), I'd have left it; but I'm a multi-desktop person (like having a change by using a different desktop some days).

FYI:  *It's useful if we know your actual release details, the last five releases of Lubuntu have used LXQt so providing that allows us to be more precise.*

I am currently using Lubuntu 20.04 LTS.

So even after "sudo apt-get remove ubuntu-gnome-desktop" and "sudo apt autoremove" the system will still be issuing updates for Gnome? Is that it?

Actually I don't have the disk space. I am lucky that this partition is for testing purposes, but it's always good to learn how Linux works.

I have chosen the Lubuntu distribution because it's more lightweight and snappier than Ubuntu.

---

### Post by guiverc on 2021-02-02
My prior message was giving what I would have done.

As you

```
apt install gnome-tweaks
```

I would have fixed with

```
apt remove gnome-tweaks
apt autoremove
```

ie. remove what you installed.  The other packages installed (because of dependencies) will get cleaned up by the subsequent `apt autoremove` command.

Instead you removed a different package, thus some parts may still remove.  I could look up (I provided packages.ubuntu.com links previously, but it needs your exact release which I didn't know, so I used my own, being *hirsute* in my example links)

You may have achieved the same thing.. If on your system, I'd look at your `apt` logs (`/var/log/apt/history.log`) to check, OR view packages (`dpkg -l |grep gnome`) or many other ways.. but I would base the removal command on what you installed (`gnome-tweaks`)

---

### Post by username2758 on 2021-02-03
@**guiverc**

Thank you very much for your help, it's much appreciated. I am not a Linux expert so it's pretty confusing to me.

Right after installing gnome-tweaks, I tried "sudo apt remove gnome-tweaks" but it didn't work, so upon research I found "sudo apt remove ubuntu-gnome-desktop" and from I could see a lot of files were deleted in the process.

Here is the output for "dpkg -l |grep gnome" :
```
dpkg -l |grep gnome
rc  chrome-gnome-shell                            10.1-5                                all          GNOME Shell extensions integration for web browsers
ii  gkbd-capplet                                  3.26.1-1                              amd64        GNOME control center tools for libgnomekbd
ii  gnome-accessibility-themes                    3.28-1ubuntu1                         all          High Contrast GTK+ 2 theme and icons
ii  gnome-control-center                          1:3.36.4-0ubuntu2                     amd64        utilities to configure the GNOME desktop
ii  gnome-control-center-data                     1:3.36.4-0ubuntu2                     all          configuration applets for GNOME - data files
ii  gnome-control-center-faces                    1:3.36.4-0ubuntu2                     all          utilities to configure the GNOME desktop - faces images
ii  gnome-desktop3-data                           3.36.8-0ubuntu1                       all          Common files for GNOME desktop apps
ii  gnome-icon-theme                              3.12.0-3                              all          GNOME Desktop icon theme
ii  gnome-keyring                                 3.36.0-1ubuntu1                       amd64        GNOME keyring services (daemon and tools)
ii  gnome-keyring-pkcs11:amd64                    3.36.0-1ubuntu1                       amd64        GNOME keyring module for the PKCS#11 module loading library
rc  gnome-menus                                   3.36.0-1ubuntu1                       amd64        GNOME implementation of the freedesktop menu specification
ii  gnome-online-accounts                         3.36.0-1ubuntu1                       amd64        service to manage online accounts for the GNOME desktop
rc  gnome-session-common                          3.36.0-2ubuntu1                       all          GNOME Session Manager - common files
ii  gnome-settings-daemon                         3.36.1-0ubuntu1                       amd64        daemon handling the GNOME session settings
ii  gnome-settings-daemon-common                  3.36.1-0ubuntu1                       all          daemon handling the GNOME session settings - common files
rc  gnome-shell                                   3.36.4-1ubuntu1~20.04.2               amd64        graphical shell for the GNOME desktop
ii  gnome-system-monitor                          3.36.1-0ubuntu0.20.04.1               amd64        Process viewer and system resource monitor for GNOME
ii  gnome-themes-extra:amd64                      3.28-1ubuntu1                         amd64        Adwaita GTK+ 2 theme — engine
ii  gnome-themes-extra-data                       3.28-1ubuntu1                         all          Adwaita GTK+ 2 theme — common files
ii  gnome-user-docs                               3.36.2+git20200704-0ubuntu0.1         all          GNOME user docs
ii  language-selector-gnome                       0.204.2                               all          Language selector for Ubuntu
ii  libgnome-bluetooth13:amd64                    3.34.3-0ubuntu1                       amd64        GNOME Bluetooth tools - support library
ii  libgnome-desktop-3-19:amd64                   3.36.8-0ubuntu1                       amd64        Utility library for loading .desktop files - runtime files
ii  libgnomekbd-common                            3.26.1-1                              all          GNOME library to manage keyboard configuration - common files
ii  libgnomekbd8:amd64                            3.26.1-1                              amd64        GNOME library to manage keyboard configuration - shared library
ii  libpam-gnome-keyring:amd64                    3.36.0-1ubuntu1                       amd64        PAM module to unlock the GNOME keyring upon login
ii  libsoup-gnome2.4-1:amd64                      2.70.0-1                              amd64        HTTP library implementation in C -- GNOME support library
ii  network-manager-gnome                         1.8.24-1ubuntu3                       amd64        network management framework (GNOME frontend)
ii  pinentry-gnome3                               1.1.0-3build1                         amd64        GNOME 3 PIN or pass-phrase entry dialog for GnuPG
```

I definitely want to delete them all, but how do I do that? 

As I said before, I have installed only two Gnome-based software separately, the System Monitor and Gedit. I'd like to keep those.

---

