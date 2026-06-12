---
title: "Download packages for actave"
date: 2008-08-22
forum: Education &amp; Science
---

### Post by 7raTEYdCql on 2008-08-22
How do i download packages that are meant for octave. I know that octave packages are written individually. But from where must one download these packages. From the Repositories???

---

### Post by xeth_delta on 2008-08-22
The package management system takes care of downloading and installing the programs/packages. All you have to do is choose what you need.

There are several alternatives. If you want a graphical interface, you can use Synaptic (for Gnome), Adept (for KDE). There you can search for octave and the related packages will be shown.

If you prefer the command line, you can:

```
apt-cache search search_term
```
or
```
aptitude search search_term
```
for searching, and to install
```
apt-get install package_name
```
or
```
aptitude install package_name
```

A lot more information here:
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)
and here:
[https://help.ubuntu.com/community/SoftwareManagement](https://help.ubuntu.com/community/SoftwareManagement)

---

