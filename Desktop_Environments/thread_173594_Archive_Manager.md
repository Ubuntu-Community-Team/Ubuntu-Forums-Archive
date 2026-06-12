---
title: "Archive Manager"
date: 2006-05-10
forum: Desktop Environments
---

### Post by Landy Mann on 2006-05-10
Hi 
I'm new to linux and when i try to install .deb and .rpm files archive manager says 
"Archive type not supported" am i doing somthing wrong or is there a problem with ubuntu

thanks

Landy Mann

---

### Post by matthewstory on 2006-05-10
I take it that you're trying to install .deb files using the archive manager.  .deb is a debian package file and its not strictly speaking just an archive, to open .deb files you have to use the dpkg utility, to install it would be dpkg -i <package name> in the command line.  RPMs have no place in a debian distribution its just generally not how things are done, that's more Suse or RedHat's thing.  I'm guessing that you've downloaded this stuff from some website, instead please use the Synaptic package manager (System > Install Programs (I believe)) or apt-get or aptitude in the command line.

---

### Post by Ramses de Norre on 2006-05-10
```
sudo apt-get install alien && alien /path/to/package 
```
coverts rpm's to deb's which are installable with dpkg.

---

### Post by Landy Mann on 2006-05-11
Thank I will look into it

Landy Mann](*,)

---

