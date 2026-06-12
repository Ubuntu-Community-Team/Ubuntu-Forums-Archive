---
title: "Can't install KDE4"
date: 2008-01-17
forum: Desktop Environments
---

### Post by Moonfrost on 2008-01-17
I tried installing KDE4 from synaptic but I get a bunch of broken dependencies and thus kde4 won't install at all...well, I went and tried the same thing but through a terminal with 

```
sudo apt-get install kde4
```

and this is what I get...

```
username@username:~$ sudo apt-get install kde4
[sudo] password for username:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  kde4: Depends: kde4-amusements (>= 3.2~gutsy1) but it is not going to be installed
        Depends: kdeaccessibility-kde4 (>= 4:4.0.0) but it is not going to be installed
        Depends: kdeadmin-kde4 (>= 4:4.0.0) but it is not going to be installed
        Depends: kdeartwork-kde4 (>= 4:4.0.0) but it is not going to be installed
        Depends: kdemultimedia-kde4 (>= 4:4.0.0) but it is not installable
        Depends: kdenetwork-kde4 (>= 4:4.0.0) but it is not installable
        Depends: kdeutils-kde4 (>= 4:4.0.0) but it is not installable
E: Broken packages
```

---

### Post by Fixxxer on 2008-01-17
You should follow these instructions: [HTML]http://kubuntu.org/announcements/kde-4.0.php[/HTML]

---

### Post by Moonfrost on 2008-01-17
> **Fixxxer said:**
> You should follow these instructions: [HTML]http://kubuntu.org/announcements/kde-4.0.php[/HTML]

Ok, but isn't that if I have a previous installation of KDE? say KDE 3.5.8? because I don't have a previous installation of KDE at all...I'm using Gnome...

---

### Post by Fixxxer on 2008-01-18
> **Moonfrost said:**
> Ok, but isn't that if I have a previous installation of KDE? say KDE 3.5.8? because I don't have a previous installation of KDE at all...I'm using Gnome...
That doesn't matter. I've installed it that way, once with kde and once with gnome installed.

---

### Post by sauronsmatrix on 2008-01-18
i installed kubuntu 8.04 alpha three, followed [these instructions]("http://kubuntu.org/announcements/kde-4.0.php"), and they worked.

---

