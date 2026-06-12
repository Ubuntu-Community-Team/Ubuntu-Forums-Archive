---
title: "Would someone be so kind to ..."
date: 2009-04-19
forum: General Help
---

### Post by .:PiXi²:. on 2009-04-19
Hi

A binary file got damaged and I want to simply replace it by a good copy.
Could anyone of you be so kind to upload these files for me?

/usr/lib/libQtNetwork.so.4
/usr/lib/libQtNetwork.so.4.4
/usr/lib/libQtNetwork.so.4.4.3

Thanks in advance.

---

### Post by Titan8990 on 2009-04-19
Just do: 

sudo dpkg -S /usr/lib/libQtNetwork.so


And reinstall the package it says that it came from.

---

### Post by .:PiXi²:. on 2009-04-19
Thanks Titan8990

dpkg told me it came from libqt4-network, a simple reinstall didn't solved it. So I completely cleared everything that had something to do with it, it may be stupid, but thought it could be related to another binary file. After completely removing libqt4-network, libqt4-assistant, libqt4-core, libqt4-gui, libqt4-qt3support, qt4-qtconfig, skype and VirtualBox. I installed the packages again and the problem is still there.

Does someone knows the solution for "undefined symbol: _ZN14QObjectPrivate15checkWindowRoleEv" in /usr/lib/libQtNetwork.so.4.4.3 ?
All help is welcome.

---

