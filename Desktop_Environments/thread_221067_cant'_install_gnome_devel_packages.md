---
title: "cant' install gnome devel packages"
date: 2006-07-22
forum: Desktop Environments
---

### Post by lizardking on 2006-07-22
this is the problem:
```
lizardking@lizard:~$ aptinstall libgnome-desktop-dev
Lettura della lista dei pacchetti in corso... Fatto
Generazione dell'albero delle dipendenze in corso... Fatto
Alcuni pacchetti non possono essere installati. Questo può voler
dire che è stata richiesta una situazione impossibile oppure, se
si sta usando la distribuzione "unstable", che alcuni pacchetti
richiesti non sono ancora stati creati o rimossi da incoming.

Poiché è stata richiesta solo una singola operazione è molto facile che
il pacchetto semplicemente non sia installabile, si consiglia
di inviare un "bug report" per tale pacchetto.
Le seguenti informazioni possono aiutare a risolvere la situazione:

I seguenti pacchetti hanno dipendenze non soddisfatte:
  libgnome-desktop-dev: Dipende: libgnomeui-dev (>= 2.6.0) ma non sta per essere installato
E: Pacchetto non integro

```

Some help? I cannot install the gnome devel packages.. :-k 
I think there is a source.list problem

---

### Post by mlind on 2006-07-22
Translation would be nice, but make sure you have main, resricted, multiverse and universe repositories enabled.
[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

---

### Post by lizardking on 2006-07-24
seem that I have all the repository you post there. and so?
this is my sources.list
```
lizardking@lizard:~$ cat /etc/apt/sources.list
# Dapper Final Release Repository
deb-src http://de.archive.ubuntu.com/ubuntu dapper main

deb-src http://de.archive.ubuntu.com/ubuntu dapper restricted

deb-src http://de.archive.ubuntu.com/ubuntu dapper universe

deb http://de.archive.ubuntu.com/ubuntu/ dapper multiverse universe restricted main
deb-src http://de.archive.ubuntu.com/ubuntu dapper multiverse

# Dapper Security Updates
deb http://de.archive.ubuntu.com/ubuntu dapper-security main
deb-src http://de.archive.ubuntu.com/ubuntu dapper-security main

deb http://de.archive.ubuntu.com/ubuntu dapper-security restricted
deb-src http://de.archive.ubuntu.com/ubuntu dapper-security restricted

deb http://de.archive.ubuntu.com/ubuntu dapper-security universe
deb-src http://de.archive.ubuntu.com/ubuntu dapper-security universe

deb http://de.archive.ubuntu.com/ubuntu dapper-security multiverse
deb-src http://de.archive.ubuntu.com/ubuntu dapper-security multiverse

# Dapper Bugfix Updates
deb http://de.archive.ubuntu.com/ubuntu dapper-updates main
deb-src http://de.archive.ubuntu.com/ubuntu dapper-updates main

deb http://de.archive.ubuntu.com/ubuntu dapper-updates restricted
deb-src http://de.archive.ubuntu.com/ubuntu dapper-updates restricted

deb http://de.archive.ubuntu.com/ubuntu dapper-updates universe
deb-src http://de.archive.ubuntu.com/ubuntu dapper-updates universe

deb http://de.archive.ubuntu.com/ubuntu dapper-updates multiverse
deb-src http://de.archive.ubuntu.com/ubuntu dapper-updates multiverse

# Dapper Backports (new software versions, provided by the Ubuntu Backports Project)
deb http://de.archive.ubuntu.com/ubuntu dapper-backports main
deb-src http://de.archive.ubuntu.com/ubuntu dapper-backports main

deb http://de.archive.ubuntu.com/ubuntu dapper-backports restricted
deb-src http://de.archive.ubuntu.com/ubuntu dapper-backports restricted

deb http://de.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
deb-src http://de.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse

deb http://de.archive.ubuntu.com/ubuntu dapper-backports universe
deb-src http://de.archive.ubuntu.com/ubuntu dapper-backports universe

deb http://de.archive.ubuntu.com/ubuntu dapper-backports multiverse
deb-src http://de.archive.ubuntu.com/ubuntu dapper-backports multiverse

deb http://archive.canonical.com/ubuntu dapper-commercial main

```

---

### Post by philippe_carlo on 2006-07-24
try
```

sudo apt-get update
sudo apt-get install -f

```

---

### Post by lizardking on 2006-07-24
Done but nothing! I have still the problem!

---

### Post by mlind on 2006-07-24
> **lizardking said:**
> Done but nothing! I have still the problem!

```

$ apt-cache policy libgnome-desktop-dev
libgnome-desktop-dev:
  Installed: (none)
  Candidate: 2.14.2-0ubuntu1
  Version table:
     2.14.2-0ubuntu1 0
        500 http://archive.ubuntu.com dapper-updates/main Packages
     2.14.1.1-0ubuntu2 0
        500 http://archive.ubuntu.com dapper/main Packages

```

Latest version of the package is on dapper-updates, install it using
```

sudo aptitude install libgnome-desktop-dev

```

Change to another APT mirror if aptitude doesn't find it.

---

### Post by lizardking on 2006-07-26
Seems to be all ok!

Thank you very much!

---

