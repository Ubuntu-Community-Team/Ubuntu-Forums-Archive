---
title: "Ubuntu 10.10 libQt errors??"
date: 2011-05-16
forum: Desktop Environments
---

### Post by paulysa1969 on 2011-05-16
Hi there. 

I am unable to run Skype, Quantum GIS 1.4 and VirtualBOX  4.0.4.
So I ran the startup commands for each in a standard (sudo.....) as well as root terminal with the same results.

I seem to be  getting similar libQt*.so.4 undefined symbol errors as seen below:
 

pauly@PaulSamsungNC10:~$ skype
skype: symbol lookup error: /usr/lib/libQtDBus.so.4: undefined symbol: _ZN14QObjectPrivate15checkWindowRoleEv


pauly@PaulSamsungNC10:~$ qgis
 qgis: symbol lookup error: /usr/lib/libQtSvg.so.4: undefined symbol: _ZN14QObjectPrivate15checkWindowRoleEv


pauly@PaulSamsungNC10:~$ VirtualBox
VirtualBox: supR3HardenedMainGetTrustedMain: dlopen("/usr/lib/virtualbox/VirtualBox.so",) failed: /usr/lib/libQtOpenGL.so.4: undefined symbol: _ZN14QWidgetPrivate15checkWindowRoleEv
 

I would appreciate some pointers to resolve these errors? :confused:

Thanks
Paul

---

