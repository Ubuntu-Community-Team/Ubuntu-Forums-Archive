---
title: "Add/Remove Programs in Debian?"
date: 2007-08-12
forum: Debian
---

### Post by fd9_ on 2007-08-12
Quick question: Is there a way I can get the Add/Remove application in Debian?
Thanks.

---

### Post by benanzo on 2007-08-12
```
sudo apt-get install gnome-app-install
```

---

### Post by Caraibes on 2007-08-24
-Why not use Synaptic ??? It is very good...

---

### Post by super.rad on 2007-08-27
I am using Debian 4.0 and when i try and install this it says 
```
 Package gnome-app-install is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package gnome-app-install has no installation candidate

```
Does anyone know how i can install this?

---

### Post by Pancetilla on 2007-08-27
Gnome-app-install is not in "etch" (stable), it's in "lenny" (unstable) actually.

So you must change your /etc/apt/sources.list. and then apt-get update. It should be available then.

You can get the .deb directly from [here]("http://packages.debian.org/unstable/gnome/gnome-app-install"), but it will be messy, having the rest of debian still in "stable"

---

### Post by kellemes on 2007-08-27
> **Caraibes said:**
> -Why not use Synaptic ??? It is very good...

Agree..
**If** you have the need to work graphically synaptic does it's job fine..

---

### Post by super.rad on 2007-08-27
> **Pancetilla said:**
> Gnome-app-install is not in "etch" (stable), it's in "lenny" (unstable) actually.

So you must change your /etc/apt/sources.list. and then apt-get update. It should be available then.

You can get the .deb directly from [here]("http://packages.debian.org/unstable/gnome/gnome-app-install"), but it will be messy, having the rest of debian still in "stable"

ah right cant be bothered with mixing stable and unstable, im fine with synaptic but just thought i'd install it if it was easy, thanks

---

