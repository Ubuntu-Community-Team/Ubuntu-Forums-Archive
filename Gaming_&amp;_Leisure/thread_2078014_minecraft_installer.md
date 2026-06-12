---
title: "minecraft installer"
date: 2012-10-29
forum: Gaming &amp; Leisure
---

### Post by homerhomer on 2012-10-29
minecraft install script that installs minecraft and needed libraries as user. 

** Don't run as root **
** Backup all your files first **
** You have to run both scripts for this to work because lwjgl and java7 **


All the files with this script are installed in use space including the java files  

* Installs Oracle Java7
* Installs Minecraft Jar files
* Crates and adds Unity icon 
* Updates the lwjgl files for java7


3 steps to install  ( ** backup your minecraft files first ** )

1) Run mc_install  ( don't use root ) 
2) Open minecraft (it will but searchable in unity ) and login and let it sync the files needed to run minecraft. Once this is done you'll notice that you get a black screen. Just close minecraft run the last script. 
3) Run mc_install_lwjgl_update
  
If you wish to uninstall this just delete the following

just remove the following files and folders
~/Games/minecraft/
~/.local/share/applications/minecraft.desktop

Enjoy!

---

### Post by homerhomer on 2013-03-06
Fixed and updated installer to use the latest Java 7 update 17
Script is now just one file.

---

