---
title: "Gnome installation messed up Unity in Ubuntu 16.04"
date: 2020-05-27
forum: Desktop Environments
---

### Post by balaena on 2020-05-27
Hi,

I wanted to use Gnome with Ubuntu 16.04, because in an older Ubuntu distribution I already had Unity and Gnome without a problem and I liked the Gnome desktop. 
  I installed it with:

 sudo apt-get install ubuntu-gnome-desktop

 In the configuration menu I then chose LightDM. 

 After successful install, things turned out to be really bad. 

 In Unity, the top menu bar and the launcher are still there but the desktop is black and displays no files. The files are displayed in the file manager though. I also can't chose a background. Minimizing windows does not work properly and from time to time the desktop freezes. 
  
 I can choose Gnome desktop, but also here the files on the desktop are gone. I cannot even choose the Desktop in the file manager 
  
 So I would rather like to remove the Gnome desktop. But is it possible to safely remove it? To me it seems that it is now intimately connected with the Unity desktop, otherwise it could not have affected the latter so much? 
  
 Or is it as simple as sudo apt-get remove ubuntu-gnome-desktop? 
  
 Or remove the package via Synaptic? 
  
 Any help would be appreciated! 
  
 Best

---

### Post by balaena on 2020-05-28
OK, I apparently have solved the problem. I say apparently because I still had a somewhat strange behavior of the file manager, but it couldn't be reproduced. I still have to observe this. I can only say what solved the problem, I actually do not understand why.


Regarding disappeared files on the desktop, I found the recommendation to run the dconf-editor


dconf-editor &#8594; org &#8594; gnome &#8594; desktop &#8594; background &#8594; show-desktop-icons


and check if it is selected. That was the case. But deselecting, selecting and exiting dconf-editor solved the problem with the desktop and with the freezing of minimized windows. It's a bit strange, because the problem with the desktop was not only the missing files, but also that no background could be selected and that there was no context menu for the desktop.


The installation of the Gnome desktop also replaced the standard fonts under Unity. Looked terrible. I replaced these fonts in the Unity Tweak Tool with the corresponding Ubuntu fonts. Now everything appears to be normal again.


As long as I don't notice anything else, I'll probably just leave Gnome alone. It seems too delicate to uninstall the package according to the following instructions.


[https://askubuntu.com/questions/767577/how-can-i-remove-gnome-desktop-environment-without-messing-unity-de-ubuntu-16](https://askubuntu.com/questions/767577/how-can-i-remove-gnome-desktop-environment-without-messing-unity-de-ubuntu-16)

---

