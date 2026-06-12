---
title: "General Question for Installing things in Ubunto..."
date: 2006-09-22
forum: Desktop Environments
---

### Post by Wheelman on 2006-09-22
Is there some sort of generic steps I can follow to install a particular program in Ubunto.  For example, I'm trying to install FlightGear Simulator on my laptop.  I go to the download page, select the "prebuilt debian package" and when it opens I am denied because some library is not found on my computer.  So ill find that library on the page, attempt to install it first, and i'll get the same message referencing some other package I'm missing.  It just seems like an endless cycle to get the stuff I need to make these programs work.  Is there some function I can use to tell it to download any supporting packages it needs automatically, or at least a generic pattern I can follow when installing things to make it so its not a hunt and search for 100 different packages?

Thanks in advance,
Wheelman
:)

---

### Post by whizbaby on 2006-09-22
Have you tried one of these:
sudo apt-get install *pkg_name* (apt-cache search *something* to look for stuff)
sudo synaptic (opens a graphical package installer)
if you need programs from a specific repository (this means neither in ubuntu main, universe or multiverse or backports) you have to append it to */etc/apt/sources.list*

---

### Post by ayoli on 2006-09-22
```
[19:14:48@ayoli.zone]:~ >$ aptitude search FlightGear
p   flightgear                           - Flight Gear Flight Simulator  
```
means it's in ubuntu repositories (universe), so you can use aptitude via the command line:
```
sudo aptitude install flightgear
```
or use synaptic package manager (in Main menu: System > Administration > Synaptic)

so "generic steps", when you want an app search first in ubuntu repos or a third party ubuntu repos to add to your /etc/apt/source.list, then install with aptitude or synaptic

---

### Post by Wheelman on 2006-09-22
Thanks! That is what i needed to know!

---

### Post by Wheelman on 2006-09-22
> **ayoli said:**
> ```
[19:14:48@ayoli.zone]:~ >$ aptitude search FlightGear
p   flightgear                           - Flight Gear Flight Simulator  
```
means it's in ubuntu repositories (universe), so you can use aptitude via the command line:

Where did you find that listed at and what part of it means its in the universe repository?

---

### Post by ayoli on 2006-09-22
in a terminal, type in :
```
sudo gedit /etc/apt/sources.list
```
you should have a line like this in this file:
```
deb http://fr.archive.ubuntu.com/ubuntu/ dapper universe multiverse
```
if there is a # at beginning of line, remove it, save file and close.
then in the terminal again type in:
```
sudo aptitude update
```
and then try again
```
sudo aptitude install flightgear
```

edit: forgot, when you want to know more about a apckage, for ex flightgear:
```
[20:22:05@ayoli.zone]:~ >$ aptitude show flightgear
```
will output:
```
Paquet : flightgear
État: non installé
Version : 0.9.10-2
Priorité : supplémentaire
Section : universe/games
Responsable : Ove Kaaven <ovek@arcticnet.no>
Taille décompressée : 5616k
Dépend: freeglut3, libalut0, libc6 (>= 2.4-1), libgcc1 (>= 1:4.1.0), libgl1-mesa-glx |
         libgl1, libglu1-mesa | libglu1, libice6, libjpeg62, libopenal0a, libsm6,
         libstdc++6 (>= 4.1.0), libx11-6, libxext6, libxi6, libxmu6, libxt6, plib1.8.4c2,
         simgear0 (>= 0.3.10-2), zlib1g (>= 1:1.2.1), fgfs-base (>= 0.9.10)
Description : Flight Gear Flight Simulator
 Flight Gear is a free and highly sophisticated flight simulator. 
 
 This package contains the runtime binaries.
```

---

### Post by whizbaby on 2006-09-22
allez-les-bleus

---

