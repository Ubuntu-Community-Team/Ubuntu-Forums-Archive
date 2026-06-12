---
title: "Menu Editor n package config path"
date: 2006-07-13
forum: Desktop Environments
---

### Post by nahas on 2006-07-13
Hi evryone,
     My menu editor doesnt seem to work,when i try to rename any item on the menu ,it doesnt work.Also there another issue ,i was trying to install ares plugin for gift ui.I get the error ....." Package libgift was not found in the pkg-config search path. Perhaps you should add the directory containing `libgift.pc' to the [COLOR="Black"]PKG_CONFIG_PATH[/COLOR] environment variable No package 'libgift' found Package libgift was not found in the pkg-config search path. Perhaps you should add the directory containing `libgift.pc' to the PKG_CONFIG_PATH environment variable No package 'libgift' found
configure: error: Library requirements (libgift >= 0.11.8 libgift < 0.12.0) not met; consider adjusting the PKG_CONFIG_PATH environment variable if your libraries are in a nonstandard prefix so pkg-config can find them."

How to add add the directory containing `libgift.pc' to the PKG_CONFIG_PATH environment variable 

pls help
regards

---

### Post by timetunnel on 2006-07-13
Regarding the problem with the menu editor: some menu items can't be renamed or deleted, because they have been installed as root. If haven't tested this, but starting the menu editor with "gksudo" from the command line could be the solution.

---

