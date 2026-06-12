---
title: "Xubuntu - GCC not installed"
date: 2006-07-19
forum: Desktop Environments
---

### Post by R.Micheals on 2006-07-19
I installed Xubuntu on my other PC(disconnected from the internet). When I want to compile something via the command line, GCC is not there. When I go into the package manager, it claims build essentials, along with other tools such as Openoffice.org are installed, although they are not. Could this be some sort of bug?

---

### Post by llamakc on 2006-07-19
I wonder if there are any packages that are not fully configured/installed yet?

You could run "apt-get -f install" to see if it continues installing packages. Do you have /usr/share/build-essential/list on your machine? Mine lists gcc and the binary is in /usr/bin.

---

