---
title: "Setting Default window manager"
date: 2012-06-18
forum: Desktop Environments
---

### Post by filmshane on 2012-06-18
Hello; 

I am on Ubuntu 10.04lucid.  I would like to know what file can I edit to change my default window manager from gnome to something else? I know there is a Default_Window_Manager file but dont know where it is. 

Please do not give my annoying gui directions as I need to do this on the comand line. I know vi. 

FilmShane

---

### Post by blackbird34 on 2012-06-18
Seems you don't know exactly what a Window Manager is though :D so I will take a few liberties (besides, i don't know vi).
Gnome 2 runs with the Compiz or Metacity WM, there is a nifty little Compiz tool called "Compiz Fusion Icon" which you can obtain and put on your Gnome Panel to toggle between Compiz and Metacity.  

Otherwise the main Desktop Environments for Ubuntu 10.04 Lucid are KDE 4., Gnome 2 and Xfce (which all are based on their own window managers). LXDE exists too but 10.04 was the first Lubuntu ever I believe.
Others like Openbox or IceWM are bare bones window managers with just a few basic tools.

To install KDE: command line : ```
sudo apt-get install kubuntu-desktop
``` (pulls in many associated apps tailored for the DE) 
                                                      ---- or (less apps) ```
sudo apt-get install kde-plasma-desktop
```
for Xfce : ```
sudo apt-get install xubuntu-desktop
```  / (barebones) ```
sudo apt-get install xfce
```
for LXDE ```
sudo apt-get install lxde
```

Although I suggest you explain more clearly what info you actually want to know.

---

