---
title: "Steam Install Fails"
date: 2015-10-18
forum: Gaming &amp; Leisure
---

### Post by bman on 2015-10-18
I am on Ubuntu Gnome 15.04 trying to install Steam. When I run "sudo apt-get install steam" I get.

```
The following packages have unmet dependencies:
 steam:i386 : Depends: libgl1-mesa-dri:i386 but it is not going to be installed
              Depends: libgl1-mesa-glx:i386 but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
```

So I run sudo apt-get install libgl1-mesa-dri:i386 and get this in result.


```
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help resolve the situation:

The following packages have unmet dependencies:
 libgl1-mesa-dri:i386 : Depends: libdrm-intel1:i386 (>= 2.4.48) but it is not going to be installed
                        Depends: libdrm-nouveau2:i386 (>= 2.4.38) but it is not going to be installed
                        Depends: libdrm-radeon1:i386 (>= 2.4.31) but it is not going to be installed
                        Depends: libdrm2:i386 (>= 2.4.38) but it is not going to be installed
 libonline-accounts-client1 : Depends: libqt5gui5 (>= 5.0.2) but it is not going to be installed or
                                       libqt5gui5-gles (>= 5.0.2) but it is not going to be installed
 liboxideqtcore0 : Depends: libqt5gui5 (>= 5.4.0) but it is not going to be installed or
                            libqt5gui5-gles (>= 5.4.0) but it is not going to be installed
 libpoppler-qt5-1 : Depends: libqt5gui5 (>= 5.0.2) but it is not going to be installed or
                             libqt5gui5-gles (>= 5.0.2) but it is not going to be installed
 libqmenumodel0 : Depends: libqt5gui5 (>= 5.0.2) but it is not going to be installed or
                           libqt5gui5-gles (>= 5.0.2) but it is not going to be installed
 libqt5multimedia5 : Depends: libqt5gui5 (>= 5.2.0) but it is not going to be installed or
                              libqt5gui5-gles (>= 5.2.0) but it is not going to be installed
 libqt5quick5-gles : Depends: libqt5gui5 (>= 5.4.1) but it is not going to be installed or
                              libqt5gui5-gles (>= 5.4.1) but it is not going to be installed
 qml-module-qtorganizer : Depends: libqt5gui5 (>= 5.0.2) but it is not going to be installed or
                                   libqt5gui5-gles (>= 5.0.2) but it is not going to be installed
 qml-module-qtquick-layouts : Depends: libqt5gui5 (>= 5.3.0) but it is not going to be installed or
                                       libqt5gui5-gles (>= 5.3.0) but it is not going to be installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
```

Any ideas or suggestions?

---

### Post by MikeCyber on 2015-10-19
Did you install your proprietary graphics drivers? AMD, Nvidia etc.

---

### Post by bman on 2015-10-19
> **MikeCyber said:**
> Did you install your proprietary graphics drivers? AMD, Nvidia etc.

I did, through Additional Drivers, then I installed the Open Source Nvidia ones (at least how they show up in Addtional Drivers, version 355.11). Which seems to be the latest drivers.

---

### Post by Bucky Ball on 2015-10-19
Please use code tags when posting terminal stuff. See the last link in my signature.

---

### Post by MikeCyber on 2015-10-21
Looks like a mess. Remove the opensource drivers and reinstall the proprietary.

---

### Post by bman on 2015-10-21
> **MikeCyber said:**
> Looks like a mess. Remove the opensource drivers and reinstall the proprietary.

As I said, I had those installed same issue, I then upgraded to Open Source. So going back to proprietary isn't going to change anything.

Nonetheless I should be upgraded to 15.10 soon enough so we will see what happens then.

---

### Post by MikeCyber on 2015-10-22
of course the proprietary work. But unluckily synaptic has several broken versions.- (really sick) Myself the first was broken but second worked. After initial fresh install, I do all updates directly from Nvidia download. Says updating driver, never had problems.

---

### Post by Chris on 2015-10-22
Sometimes "apt-get -f install" can sort out weird dependency issues. Not always but it should be one of the first things to try when you see stuff like that.

---

