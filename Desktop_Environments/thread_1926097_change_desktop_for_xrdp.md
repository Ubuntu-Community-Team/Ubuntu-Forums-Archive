---
title: "change desktop for xrdp"
date: 2012-02-15
forum: Desktop Environments
---

### Post by stn21 on 2012-02-15
Hi,

I often work with xrdp on oneiric desktop and server. 

For that purpose unity is not really a good desktop so I would like to change oneiric including xrdp to another desktop. 

On the console that is really easy, just ```
apt-get install gnome-shell
``` or ```
apt-get install lbuntu-desktop
```, then you can choose a different session on the login-screen.

Unfortunately that does not change the desktop for xrdp. That either stays unity or becomes really messed up, depending on which other desktops you install. 

Also there is no obvious way to restore it. Once it becomes messed up it stays messed up. The only way to get it running again is to reinstall ubuntu.

Reinstalling xrdp, unity, unity-2d, gnome-shell and xserver-xorg does not restore a working state. Same for dpkg-reconfigure. For now I am assuming that reinstalling some other package(s) will do the trick but I have no idea which ones.

Is there a non-fiddling way on ubuntu 11.10 to change xrdp's desktop to for example gnome-shell?
Is there a non-fiddling way restore xrdp to its original state with unity-desktop?

THX, stn

---

### Post by forsubhi on 2012-02-15
do you try sudo apt-get install kubuntu-desktop

---

### Post by stn21 on 2012-02-16
> **forsubhi said:**
> do you try sudo apt-get install kubuntu-desktop

Tried that
apt-get install kubuntu-desktop
# then to be safe:
apt-get install --reinstall xrdp

Does not change anything. In xrdp I get the standard ubuntu-Desktopbackground with a rudimentary menu-bar at the top. The "File"-menü contains "new window" , "new folder" , "new document" , "connect to server". There are also menus "Edit", "View", "Go to" , "Bookmarks", "Help"

The latter is what is needed here :confused: There is not even a way to open a console.

---

### Post by stn21 on 2012-02-16
I am reeeeally tired of all these unity-related issues. Maybe ubuntu 12.04 will include a desktop that actually works :roll:

---

### Post by suseno on 2012-10-24
Yeah... that's also my problem when logging in from remote using xRDP: **Can't Choose Desktop Enviroment**

---

