---
title: "Do we require all three steps to install kubuntu fully?"
date: 2006-07-05
forum: Desktop Environments
---

### Post by kazuya on 2006-07-05
How to Install
There are different packages to be installed to acquire Kubuntu from an Ubuntu installation depending on which packages you want. Below are the three possible choices, or "routes", to go down; the packages below are metapackages -- they depend upon other, "real", packages, and with their installation they pull them in. For details on installing packages methods, see the wiki page InstallingSoftware. The options are as follows: 

(i) kubuntu-desktop -- This is the recommended metapackage to install; the full Kubuntu installation, with all the Kubuntu recommended packages. This includes OpenOffice, Kontact, Konversation, amaroK, K3B, and others. 

(ii) kde -- This will install the following KDE packages: kde-amusements, kdeaccessibility, kdeaddons, kdeadmin, kdeartwork, kdegraphics, kdemultimedia, kdenetwork, kdepim, kdesdk, kdeutils, kdewebdev, kdevelop3 and the kde-core metapackage (see details below). 

(iii) kde-core --- This will install the core -- the bare-minimum required-- of KDE. That is, kdebase, kdelibs, arts and fontconfig. 

If you choose to not install kubuntu-desktop, then you can still get all the Kubuntu-specific tweaks by installing the kubuntu-default-settings package. 

Do we require all three steps to fully install kubuntu fully unto our Ubuntu install, as just kubuntu alone seems like certain things or desktop appearrance just doesn't work. etc..  Mepis for kde feels speedier and more put together.. than kubuntu to me..

Now Ubuntu has me converted almost totally.., but not kubuntu... I need kde for superkaramba and certain ease of use..

Or do we require just the first step alone?

---

### Post by Jucato on 2006-07-05
You don't need to do all of them. You can just pick one. the smallest choice will be installing kubuntu-desktop. Just remember to use aptitude instead of apt-get so that you could easily remove it later, if you want.

```

sudo aptitude update
sudo aptitude install kubuntu-destkop

```

About Kubuntu and MEPIS, you have to remember that MEPIS is a pure KDE distro, and Kubuntu is KDE on top of Ubuntu (minus GNOME). So in some ways, Kubuntu does not **yet** yet have the same level of "KDE" polish that MEPIS has. But it's heading towards that direction, hopefully. :D

---

