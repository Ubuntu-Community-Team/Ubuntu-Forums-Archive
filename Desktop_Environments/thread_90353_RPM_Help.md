---
title: "RPM Help"
date: 2005-11-14
forum: Desktop Environments
---

### Post by fatal.serpent on 2005-11-14
How do I install from a rpm. Help!

---

### Post by fatal.serpent on 2005-11-14
Help!!!

---

### Post by krye on 2005-11-14
Use alien to convert and install it as a .deb

```
sudo apt-get install alien
```

and then just "alien file.rpm"

---

### Post by abou on 2005-11-14
Essentially what Krye said.  The RPM you downloaded is converted to a DEB package using Alien and then installed like any other Debian package.

---

### Post by fatal.serpent on 2005-11-14
What is alien?
SRY I'm new to this.

---

### Post by arnieboy on 2005-11-14
[QUOTE=fatal.serpent]What is alien?
SRY I'm new to this.[/QUOTE]
alien is a software which u can use to convert rpm's to debs. ubuntu can only install deb packages (not rpm's).
so after u install alien u wud do the following:
```
sudo alien <package.rpm>
```
and then try and install it with 
```
sudo dpkg -i <packagename.deb>
```
chances are that u will have lots of dependency issues when trying to do that... hence converting a rpm to a deb with alien and then trying to install it is not always a good idea. 
what package (name of the package) that are u trying to install?

---

