---
title: "Warning to Kubuntu users re. Qt 4.6 RC"
date: 2009-11-21
forum: Desktop Environments
---

### Post by HTML-insane on 2009-11-21
Don't do it. You will lose all sound to all your KDE applications. Read below if, like me, you went ahead and did it [stupid]. Otherwise, stop reading.

We're going to downgrade Qt from 4.6 to 4.5. This is going to be painful, so be prepared, make sure you're not going to e.g. run out of battery power or lose your internet connection for some reason or another etc.
First, if you've done what I have then you'll recognize this command:
```
sudo add-apt-repository ppa:kubuntu-ppa/experimental
```
This doesn't add the repository to /etc/apt/sources.list, though, so don't bother looking there. It creates a new file in /etc/apt/sources.list.d/. To remove it, do:
```
sudo rm /etc/apt/sources.list.d/kubuntu-ppa-experimental-karmic.list
```
Unfortunately for you, this won't downgrade the Qt packages on its own, so keep up.
To downgrade your packages, you'll have to do some rather gritty work. Do:
```
sudo apt-get remove libqtcore4
```
Then accept the changes. Yes, it WILL remove all your KDE packages. Hey, don't look at me - the scorn of experimental packages for you.
When it asks if you want to stop KDM, **for goodness sake NO.**
When it's done churning through all of that, you're good to re-install stuff. Do:
```
sudo apt-get install kubuntu-desktop
```
Or, if you're like me and using wicd:
```
sudo apt-get install kubuntu-desktop wicd
```
Accept all those changes and reboot. You'll have to re-install non-standard-installation KDE packages yourself, though... oh, and maybe skype too.

---

### Post by captaincrook on 2009-11-21
I used aptitude to downgrade my QT Packages from 4.6 beta to the Kamric defaults. Instead of uninstalling everything, it will downgrade the other packages for you so nothing is removed. After removing the repo, and updating, try something like this **(Note this is from the Kubuntu Backport PPA, so if you have that enabled, this will work)**:

```
sudo aptitude install libqtcore4=4.5.3really4.5.2-0ubuntu1
```

Although I myself downgraded libqt4-dbus to get everything else downgraded, that should work as well. Afterwards, it should give you a dependency message, asking what it will attempt to do, which is/was downgrade other QT packages. Read the messages carefully.

---

### Post by HTML-insane on 2009-11-21
> **captaincrook said:**
> I used aptitude to downgrade my QT Packages from 4.6 beta to the Kamric defaults. Instead of uninstalling everything, it will downgrade the other packages for you so nothing is removed. After removing the repo, and updating, try something like this **(Note this is from the Kubuntu Backport PPA, so if you have that enabled, this will work)**:

```
sudo aptitude install libqtcore4=4.5.3really4.5.2-0ubuntu1
```

Although I myself downgraded libqt4-dbus to get everything else downgraded, that should work as well. Afterwards, it should give you a dependency message, asking what it will attempt to do, which is/was downgrade other QT packages. Read the messages carefully.

I tried this myself, but Aptitude actually complained at me that it wanted to uninstall all my KDE/Qt apps anyway. That's why I suggested to uninstall libqtcore4 and re-install kubuntu-desktop: the effects were, for all intents and purposes, the same.
That was my experience, anyway...

---

### Post by Zorael on 2009-11-22
I just downgraded the **phonon-backend-xine** package from the one in kubuntu-ppa/experimental to the one in Karmic main, as the terminal output of programs trying to play sound suggested something was wrong with **/usr/lib/qt4/plugins/phonon_backend/phonon_xine.so**, such as when trying to go into the Multimedia section in System Settings. Then I forbade aptitude from updating to that version, and it's currently working fine. If you're using Synaptic (or whatever) to update packages, you'll have to use its package-forbidding measures to keep the package at the version you want it, as I don't think they listen to eachother.
```
$ sudo aptitude install phonon-backend-xine=4:4.3.1-4ubuntu1
$ sudo aptitude forbid-version phonon-backend-xine
```

Kopete is once more chiming happily.


edit: The error output was as follows, for people searching the forums for it.
```
systemsettings: symbol lookup error: /usr/lib/qt4/plugins/phonon_backend/phonon_xine.so: undefined symbol: _ZN9QHashData13detach_helperEPFvPNS_4NodeEPvEPFvS1_Ei
```

---

