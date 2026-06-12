---
title: "Enabling Lancelot KDE launcher"
date: 2009-01-22
forum: General Help
---

### Post by brm on 2009-01-22
I have installed the Lancelot KDE launcher package but am unable to enable it. I have done a fair amount of STFU but can't find what I am missing.

I would be grateful if someone could post instructions on enabling Lancelot.

Here is the environment I am working in:

```
bruce@Xenophon:~$ uname -a
Linux Xenophon 2.6.27-9-generic #1 SMP Thu Nov 20 22:15:32 UTC 2008 x86_64 GNU/Linux
bruce@Xenophon:~$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 8.10
Release:        8.10
Codename:       intrepid
bruce@Xenophon:~$ dpkg -l | grep -E "lancelot|kde-nightly"
ii  kde-nightly                                           1.9                                                   Project Neon (KDE Nightly)
ii  kde-nightly-google-gadgets                            0.10.5~svn1074-0neon1                                 google gadgets for linux
ii  kde-nightly-kdebase                                   20090121+svn914665-0neon1                             runtime components from the official KDE release
ii  kde-nightly-kdegraphics                               20090121+svn914665-0neon1                             KDE graphic applications (nightly build)
ii  kde-nightly-kdelibs                                   20090121+svn914665-0neon1                             core libraries for all KDE 4 applications
ii  kde-nightly-kdemultimedia                             20090121+svn914665-0neon1                             KDE multimedia applications (nightly build)
ii  kde-nightly-kdenetwork                                20090121+svn914665-0neon1                             KDE network applications (nightly build)
ii  kde-nightly-kdepimlibs                                20090121+svn914665-0neon1                             core libraries for KDE PIM 4 applications
ii  kde-nightly-kdesupport                                20090121+svn914665-0neon1                             KDESupport stuff
ii  plasmoid-lancelot                                     1.0.3~svn860641-0ubuntu2                              An alternative launcher menu plasmoid for KDE
bruce@Xenophon:~$

```

---

