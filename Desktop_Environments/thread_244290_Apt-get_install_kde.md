---
title: "Apt-get install kde ?"
date: 2006-08-26
forum: Desktop Environments
---

### Post by latebeat on 2006-08-26
I have a question,

I have ubuntu installed and I just installed kubuntu-desktop on top as well. (I want both kde and gnome). Out of curiocity I did an apt-get install kde -s and I get a huge list of new programs that are gonna be installed. Shouldn't they be installed already with kubuntu-desktop?

thanks

---

### Post by Dr. Nick on 2006-08-26
not necessarily, the kubuntu-desktop installs the basic kde desktop and the preselected packages, their are still others that can be installed that were not included in the default kubuntu

alot of the extra kde packages are language files for internationalzation and alot of dev packages that really are not usually nedded

---

### Post by aysiu on 2006-08-26
I'm sad that you used *apt-get* instead of *aptitude*, but what's done is done.

In any case, these are all metapackages--labels that point to a set of packages.

In order from smallest to largest set:

**kdebase** - the absolute bare minimum to use KDE

**kde-core** - basic but functional KDE

**kubuntu-desktop** - KDE with Ubuntu's default set of packages.

**kde** - the whole kitten kaboodle!

---

