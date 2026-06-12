---
title: "error installing compiz"
date: 2007-04-15
forum: Desktop Environments
---

### Post by iidestined on 2007-04-15
i had compiz installed and tried kiba dock. didnt' like it but it must have done something to compiz. i tried to run it but it didn't work. so i tried to reinstall following the wiki and it didn't work. i got this error:

The following packages have unmet dependencies:
  compiz-extra: Depends: compiz-extra-plugins (= 0.3.6.0-0gandalfn3) but 0.5.0.0-1~3v1ubuntu0 is to be installed
  compiz-plugins: Depends: compiz-core (= 1:0.3.6-0gandalfn11) but 1:0.5.0-1~3v1ubuntu1 is to be installed
  gnome-compiz-manager: Depends: libgnome-compiz-manager but it is not going to be installed
                        Depends: libgnome-compiz-manager but it is not going to be installed
                        Depends: compiz-gnome but it is not going to be installed
  gnome-compiz-manager-extra: Depends: libgnome-compiz-manager but it is not going to be installed
                              Depends: compiz-gnome but it is not going to be installed
E: Broken packages

---

### Post by iidestined on 2007-04-15
bump?

---

### Post by hardkaare on 2007-04-22
Hi there.

You need the following repositories

deb [http://gandalfn.club.fr/ubuntu](http://gandalfn.club.fr/ubuntu) feisty motu
deb [http://gandalfn.club.fr/ubuntu](http://gandalfn.club.fr/ubuntu) feisty dev (this is the one you are missing!)

---

### Post by maher_79 on 2007-06-12
> **hardkaare said:**
> Hi there.

You need the following repositories

deb [http://gandalfn.club.fr/ubuntu](http://gandalfn.club.fr/ubuntu) feisty motu
deb [http://gandalfn.club.fr/ubuntu](http://gandalfn.club.fr/ubuntu) feisty dev (this is the one you are missing!)

I added this one to my "sources.list" file but still getting the dependency error below:

```
[COLOR="Red"]The following packages have unmet dependencies:
  gnome-compiz-manager-extra: Depends: libgnome-compiz-manager[/COLOR] which is a virtual package.
Resolving dependencies...
The following actions will resolve these dependencies:

Keep the following packages at their current version:
gnome-compiz-manager-extra [Not Installed]

Score is -10001

Accept this solution? [Y/n/q/?] y
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

It should be looking for libgnome-compiz-manager0 (that i have installed) and not libgnome-compiz-manager!!!!!!

Anyone know how to fix this? Please please :(

---

