---
title: "Stopping a Package Uninstalling"
date: 2009-05-01
forum: General Help
---

### Post by gareththered on 2009-05-01
I've recently got my Canon iP1800 printer to work, but every time I type
```
sudo apt-get -s autoremove
``` I get ```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libglib1.2ldbl libgtk1.2 cnijfilter-ip1800series libgtk1.2-common
The following packages will be REMOVED
  cnijfilter-ip1800series libglib1.2ldbl libgtk1.2 libgtk1.2-common
0 upgraded, 0 newly installed, 4 to remove and 0 not upgraded.
Remv cnijfilter-ip1800series [2.70-2]
Remv libgtk1.2 [1.2.10-18.1build2]
Remv libglib1.2ldbl [1.2.10-19build1]
Remv libgtk1.2-common [1.2.10-18.1build2]

``` As you can see, it's trying to uninstall the Canon driver package 'cnijfilter-ip1800series'.  Why?  I also recently installed the Opera browser, but that's not in the list for uninstall.  I've done nothing to either the Canon driver or Opera (or any other package) to make them either uninstall or stay installed, but the package management system treats them differently.
Does anyone have any ideas about how to get the Canon driver to stay installed.

---

### Post by brian_p on 2009-05-01
> **gareththered said:**
> 

Does anyone have any ideas about how to get the Canon driver to stay installed.

It a native .deb package? Or an rpm converted by alien. I'd remove the other packages individually with apt-get purge.

---

### Post by gareththered on 2009-05-02
Brian,

Apparently, it's an RPM converted to a DEB as Canon does not provide a DEB for their print driver.

Some of the other packages are dependencies of the Canon driver, 'libgtk1.2' for example.  Is there an issue with RPMs converted with Alien?

Gareth

---

### Post by gareththered on 2009-05-02
Just figured it out.

It was marked as an auto-installed package and as nothing was dependent on it was a candidate for removal.

I changed it to a manual-installed package with 'aptitude' and now it and it's dependencies aren't being suggested for removal.

---

