---
title: "how do i get synaptic / apt-get to ignore dependency errors?"
date: 2009-03-12
forum: General Help
---

### Post by Neo_The_User on 2009-03-12
I purposely installed apps from source and debs from other issues and now I have dependency errors and I don't care. How can I make the errors stop popping up and let me update my system? I want dependecy errors otherwise my machine doesn't do what I want it to do and if I explained what I'm doing and why, it wouldn't make a bit of difference and you most likely wouldn't understand. Ubuntu doesn't have what I want now I have what I want but every single package pretty much has dependency problems. Anyway around this? ...or do I just need to switch to gentoo since its more suited for the hardcore developers? Ugh this is so annoying!

libstdc++6 depends on gcc-4.3 but gcc-4.4 is installed. xorg-dev depends on xorg-xserver 1.5 but is not going to be installed (well duh I compiled Xorg server 1.6 from git!)

I have an important project for the mesa team so I need this fixed by tonight.

---

### Post by Neo_The_User on 2009-03-13
bump.

---

### Post by heindsight on 2009-03-13
The whole point of a package manager is to make sure everything works by making sure all dependencies of each package are installed. By circumventing the package manager, installing things the package manager doesn't know about, forcing the package manager to ignore broken dependencies, etc. you're only going to cause yourself problems. Something is going to break and you're going to have a nightmare of a time trying to fix it.

Having said that, dpkg has an option to turn dependency errors into warnings. Read the manual:
```
man dpkg
```

---

### Post by smudgy on 2013-04-01
> **heindsight said:**
> The whole point of a package manager is to make sure everything works by making sure all dependencies of each package are installed. By circumventing the package manager, installing things the package manager doesn't know about, forcing the package manager to ignore broken dependencies, etc. you're only going to cause yourself problems. Something is going to break and you're going to have a nightmare of a time trying to fix it.

Having said that, dpkg has an option to turn dependency errors into warnings. Read the manual:
```
man dpkg
```

       ```
--ignore-depends=package
```

              Ignore dependency-checking for specified packages  (actually, checking is performed, but only warnings about conflicts are given, nothing else).

---

### Post by wildmanne39 on 2013-04-01
Thread closed. Please do not post in old threads.

---

