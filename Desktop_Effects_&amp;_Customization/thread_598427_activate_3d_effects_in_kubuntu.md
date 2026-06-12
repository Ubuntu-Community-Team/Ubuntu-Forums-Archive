---
title: "activate 3d effects in kubuntu"
date: 2007-10-31
forum: Desktop Effects &amp; Customization
---

### Post by giorik on 2007-10-31
i have the kubuntu linux and i have installed beryl but i can't activate the 3d effects.. do i need drivers for the graphic card?? i have the intel i810 graphic card?? and how do i activate 3d effects??

---

### Post by smartygoldenfish on 2008-05-16
please tell about your Kubuntu distro. Which version is it? Is it Hardy or Gutsy or Edgy.
1) Install your 3D video drivers (if you haven't already)
 
 2) Install these packages either from Adept or Terminal:
open terminal
sudo apt-get install compiz 
OR
compiz-kde compizconfig-settings-manager emerald
 
 3) Do: ALT-F2 Run: compiz -replace
 
 4) Do: ALT-F2 Run: emerald -replace
 
 5) Right-click the desktop, choose "Configure Desktop > Multiple Desktops" and set it back to only show "Desktop 1".
 
 6) Then with your KMenu > Settings > Advanced Desktop Effects Settings, Click the "General Options ICON" go to "Desktop Size" and set Horizontal Virtual Size to "4", while leaving "Virtual Size" and "Number of Desktops" set to "1"
 ...and while you are there enable your Cube etc... Now you should have a working Cube, spin it with Ctrl+Alt <direction arrows>
[[http://ubuntuforums.org/showthread.php?t=582535&highlight=compiz+Kubuntu&page=4](http://ubuntuforums.org/showthread.php?t=582535&highlight=compiz+Kubuntu&page=4)

---

