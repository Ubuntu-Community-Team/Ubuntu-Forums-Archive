---
title: "how to search for a package in apt?"
date: 2005-07-12
forum: Desktop Environments
---

### Post by ^NoX on 2005-07-12
i want to search for package in apt, like i did in fedora and gentoo.
how can i do it?
thanx alot

---

### Post by ^NoX on 2005-07-12
[QUOTE=^NoX]i want to search for package in apt, like i did in fedora and gentoo.
how can i do it?
thanx alot[/QUOTE]
 nevermind.. i found a solution:
sudo apt-cache search <EXPRESSION>

---

### Post by angkor on 2005-07-12
No need for sudo when using apt-cache. You can also use grep in combination with apt-cache search...e.g:

apt-cache search firefox | grep plugin

---

### Post by az on 2005-07-12
...or use synaptic.

---

