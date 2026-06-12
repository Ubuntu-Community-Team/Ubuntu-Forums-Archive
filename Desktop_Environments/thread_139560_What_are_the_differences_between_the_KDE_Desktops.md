---
title: "What are the differences between the KDE Desktops?"
date: 2006-03-04
forum: Desktop Environments
---

### Post by nmastae on 2006-03-04
What are the differences between:

kubuntu-desktop
kde-desktop
&
kcore?

I need to figure out which one to install over my Ubuntu.

Thanks much.

---

### Post by Xian on 2006-03-04
The differences are in the applications and libraries that are selected within each of those meta-packages. Some of the ones that you have listed are not correct and would need to be changed in order to complete an actual installation.

Use apt and issue the commands below. Look at the group of packages that each selects and use that to help you determine what it is that you need and/or desire in your KDE environment. The kubuntu-desktop is what most choose as it has some packages that are more centric to how Ubuntu looks and functions.

$ sudo apt-get install kde-core
$ sudo apt-get install kde
$ sudo apt-get install kubuntu-desktop

If you want to pull in all the suggested and recommended packages within each of those categories then substitute 'aptitude' for 'apt-get' in those commands.

---

