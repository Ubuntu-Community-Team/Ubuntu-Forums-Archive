---
title: "New to Ubuntu"
date: 2009-10-20
forum: Desktop Environments
---

### Post by msaab on 2009-10-20
Hi All,
 
I recently installed Ubuntu onto my Toshiba laptop, all is going well but I am having difficulties on how to install the Unbuntu Dock Station and the 3D Desktop.
 
I found a site where it gave me the command lines but it failed to work.  
 
Could someone please shed some light on how I can install these two?
 
Many thanks
 
MS

---

### Post by undecim on 2009-10-20
Dock Station? Do you mean a Dock bar, like Mac OSX has? You can get that by installing the avant-window-navigator package, with Add/Remove, Synaptic Package Manager, or by running this command in a terminal:
```
sudo aptitude install avant-window-navigator
```For the 3D desktop, that is handled by Compiz Fusion, which is already installed, but set up to use a 2D desktop. If you want to make it 3D, install the compizconfig-settings-manager package, in the same way you installed avant-window-navigator. If you want to install both of those in one shot, run this command in a terminal: ```
sudo aptitude install avant-window-navigator compiz-fusion
```Then, under System -> Preferences -> CompizConfig Settings Manager, you can configure your desktop eye candy. To get the desktop cube (which seems to be the favorite 3D desktop setup) enable the "Desktop Cube" (at this point, it will ask you if you want to disable "Desktop Wall". Choose the option to disable it) and "Rotate Cube" options.

---

