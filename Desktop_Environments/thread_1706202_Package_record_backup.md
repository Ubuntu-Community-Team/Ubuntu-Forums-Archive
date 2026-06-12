---
title: "Package record backup"
date: 2011-03-13
forum: Desktop Environments
---

### Post by Rgibbons on 2011-03-13
Mintppc has a nice little backup tool for making a backup record of all the packages you have added since the initial linux install.

Does Ubuntu or anyone else have such a backup utility? It would be nice to have it all the packages documented somewhere in case I ever have to reinstall and figure out what packages I installed.

---

### Post by oldfred on 2011-03-13
This lists all packages, but when reinstalling it only add ones not already installed. Since it is just package names it installed the correct version for your distribution.  I run this regularly and include it in /home so it is part of my backups.

You may want to edit - for example my list still has OpenOffice, but Ubuntu is changing to Libre. If you do not want both, you have to edit your list.

from lovinglinux - use dpkg to list installed apps
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)
[http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/](http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/)

List Packages
dpkg --get-selections > ubuntu-files
Reinstall
sudo dpkg --set-selections < ubuntu-files && sudo apt-get dselect-upgrade

List with explanations of programs, not for reinstall
dpkg -l > ~/installed_programs.txt

---

### Post by oldos2er on 2011-03-13
Or with Synaptic, File, Save or Read Markings; History, etc.

---

### Post by Rgibbons on 2011-03-13
Thanks.

---

