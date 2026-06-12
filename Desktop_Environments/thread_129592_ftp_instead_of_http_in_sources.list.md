---
title: "ftp instead of http in sources.list"
date: 2006-02-14
forum: Desktop Environments
---

### Post by tburon on 2006-02-14
Hello. i have the following lines in sources.list for kubuntu.
# kubuntu.org packages for the latest KDE version (packages, GPG key: DD4D5088)
deb [http://kubuntu.org/packages/kde-latest](http://kubuntu.org/packages/kde-latest) breezy main

# kubuntu.org packages for the latest Koffice version (packages, GPG key: DD4D5088)
deb [http://kubuntu.org/packages/koffice-latest](http://kubuntu.org/packages/koffice-latest) breezy main

I am behind a firewall and have problems with http repositories, not with ftp repositories, so i change http by ftp  in all the ubuntu repositories and all is fine, except for kubuntu.
Do you know if there is another fiable repository in ftp ?.

Thanks in advance.

---

### Post by gingermark on 2006-02-14
not sure about the "-latest" versions of the repositories, but for KDE 3.5.1 try deb [ftp://bolugftp.uni-bonn.de/pub/kde/stable/3.5.1/kubuntu](ftp://bolugftp.uni-bonn.de/pub/kde/stable/3.5.1/kubuntu) breezy main
and for KOffice 1.5 Beta 1 try deb [ftp://bolugftp.uni-bonn.de/pub/kde/stable/koffice-1.5-beta1/kubuntu](ftp://bolugftp.uni-bonn.de/pub/kde/stable/koffice-1.5-beta1/kubuntu) breezy main

You can browse that ftp site, I think there is a "latest" version for KOffice. But then, just keeping an eye on [www.kubuntu.org](www.kubuntu.org) will let you know of new versions as well. Hope that helps.

---

