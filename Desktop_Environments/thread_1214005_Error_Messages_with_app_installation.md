---
title: "Error Messages with app installation"
date: 2009-07-15
forum: Desktop Environments
---

### Post by n00binberg on 2009-07-15
Error: Dependency is not satisfiable: vlc-nox (= 0.9.9a-2ubuntu1)  Error: Dependency is not satisfiable: fuseiso  Does this mean that there's something wrong with ubuntu or the installer packages?

---

### Post by ibutho on 2009-07-15
There is nothing wrong with Ubuntu. The package manager cannot find all the dependencies for the package you are trying to install. It could be that you have not setup your repositories correctly or you need to update your sources by running "sudo apt-get update".

---

### Post by n00binberg on 2009-07-15
I don't have internet access on that box, or any other box at home...Can I find updates from the repositories to download and install manually?

---

### Post by cariboo on 2009-07-15
When I'm not sure about a package and it's dependencies I always go to [Ubuntu Package Search]("http://packages.ubuntu.com/"). You can download the packages from there too.

---

