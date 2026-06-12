---
title: "ooo2.4 and ooo3.0.0 doesn't show menu items properly"
date: 2008-12-16
forum: General Help
---

### Post by kdd6 on 2008-12-16
hello,
i'm new to the forum and new to linux and very new to ubuntu.

my problem is that the version of openoffice.org 2.4 that shipped with ubuntu 8.10 does not show the menu items as text, just a line.  the drop down menus are the same.  the font menu is blank and the dialog boxes that i open are blank also.

if i click in a blank area it will highlight, if anything is there, but will not render text.  i thought that uninstalling ooo 2.4 and installing ooo 3.0.0 would give me menus, but it doesn't.

has anyone else had this problem and if you did, how did you fix the problem?

cheers,
kdd

---

### Post by TeXtonyx on 2008-12-16
No, I haven't had that problem but this file may help Openoffice 3
I installed manually.

[http://www.howtoforge.com/how-to-install-openoffice-3.0.0-on-ubuntu-8.04](http://www.howtoforge.com/how-to-install-openoffice-3.0.0-on-ubuntu-8.04)
cd desktop-integration
sudo dpkg -i -R openoffice.org3.0-debian-menus_3.0-9354_all.deb

"This works only if you have previously uninstalled Ubuntu's 
OpenOffice package (don't do this if you want to run Ubuntu's 
OpenOffice and OpenOffice 3.0.0 in parallel)! If you have not, 
you will see the following error: ..."

---

### Post by binbash on 2008-12-16
if i understand correctly, it is nvidia driver bug.Search forums for the driver version which fixes this.

---

