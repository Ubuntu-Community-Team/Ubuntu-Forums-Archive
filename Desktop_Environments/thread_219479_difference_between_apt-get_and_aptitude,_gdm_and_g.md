---
title: "difference between apt-get and aptitude, gdm and gde, kdm and kde ..."
date: 2006-07-20
forum: Desktop Environments
---

### Post by Isoss on 2006-07-20
I have ubuntu-server .. I installed it many times and each time I tried installing a desktop in a different way.
sometimes I used: apt-get install kdm and sometimes kde ... othetimes aptitde install kde some kdm ... I tried apt-get install kubuntu-desktop and ubuntu-desktop ... aptitude install gnome and all that!!!

I just dunno the difference between apt-get and aptitude! I know one thing, that when I install a desktop with aptitude I can remove it and all it's dependencies by just running aptitude remove *desktop-environment*
while in apt-get I have to remove each gnome or kde application which are usually installed with the desktop environment. So, my questions are:

1. What is the difference between aptitude and apt-get? and when each one can do better than the other.
2. what is the difference between kde, kdm, and kubuntu-desktop? when installing a desktop over an ubuntu-server, what is the best command to run? aptitude or apt-get? installing kde or kdm or kubuntu-desktop?
3. what is the difference between gde, gdm, gnome ubuntu-desktop? when installing a desktop over an ubuntu-server, what is the best command to run? aptitude or apt-get? installing gde or gdm or gnome or ubuntu-desktop?

Thanks

Isos.

---

### Post by msandersen on 2006-07-20
As far as I know, aptitude has better dependency resolution in that it keeps track of the dependencies for when you decide to remove a package. That is, apt-get will only remove the packages you specify, not all the dependency packages that were installed with it, whereas aptitude will, provided they're not used by other apps.

As for the rest, ubuntu-desktop and kubuntu-desktop are meta-packages as far as I know in that it's a list of everything in addition to the base system to make a complete ubuntu or kubuntu desktop setup with all the peripheral packages that entails for that particular environment.

---

