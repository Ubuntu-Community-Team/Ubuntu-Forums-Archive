---
title: "Where is apt-get source downloaded to?"
date: 2009-04-02
forum: General Help
---

### Post by NuNn DaDdY on 2009-04-02
I am trying to compile the latest source but I am having trouble finding the kernel source after using "apt-get source linux-image-$(uname -r)".  Where does apt-get place this file after it is downloaded?

---

### Post by mdgrech on 2009-04-02
Its not a hidden file in your home folder is it?  such as .gnome-source?  To check just press crtl-h in your home folder.

---

### Post by NuNn DaDdY on 2009-04-02
Nope, there is no such folder when I do that.

---

### Post by oldos2er on 2009-04-02
I think source goes to /usr/src . In Synaptic, right-click on an installed package, choose 'Properties,' 'Installed Files' to see where each file in a package is installed.

---

### Post by snova on 2009-04-02
From **man apt-get**:

> 
       source
           source causes apt-get to fetch source packages. APT will examine the available packages to decide which source package to fetch. [B]It will then find
           and download into the current directory[/B] the newest available version of that source package. Source packages are tracked separately from binary
           packages via deb-src type lines in the sources.list(5) file. This probably will mean that you will not get the same source as the package you have
           installed or as you could install. If the --compile options is specified then the package will be compiled to a binary .deb using dpkg-buildpackage,
           if --download-only is specified then the source package will not be unpacked.

           A specific source version can be retrieved by postfixing the source name with an equals and then the version to fetch, similar to the mechanism used
           for the package files. This enables exact matching of the source package name and version, implicitly enabling the APT::Get::Only-Source option.

           Note that source packages are not tracked like binary packages, they exist only in the current directory and are similar to downloading source tar
           balls.


---

