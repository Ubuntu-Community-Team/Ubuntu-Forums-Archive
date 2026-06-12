---
title: "installed kde4.5 from source but can't login"
date: 2010-06-06
forum: Desktop Environments
---

### Post by neoargon on 2010-06-06
In Uubuntu, I installed Kde 4.5 beta1 from source, After creating a new account. But in Gdm, only gnome is shown , no kde. After choosing xterm and logged in , when I typed plasma-desktop and kwin in the terminal, the kde desktop and window manager came . What can I do to get kde in the GDM? 
please help . This is the first time I compile KDE from source

THE WAY I COMPILED AND INSTALLED KDE ,
First I downloaded the source tarballs and extracted. created directories named Build inside each . To install a tar ball, I changed the directory to build ,which is inside the extracted tar ball . then typed the commands
cmake <address of extracted tar ball>
make
sudo make install

eg to install kdelibs ,
cd kdelibs-4.4.80
mkdir build
cd build
cmake ~/kdelibs-4.4.80
make
sudo make install

I installed extra packages when cmake asked to

I installed the KDE packages- kdelibs, kdebase, kdebase-runtime, oxygen-icons,kdeartwork, kdebase-workspace,kdemultimedia,kdeplasma-addons
And extra packages (dependancies)-phonon,  attica , soprano, libdbusmenu-qt , akonadi , acl , bison , fam , flex , hspell , shared-desktop-ontologies

Please help

---

